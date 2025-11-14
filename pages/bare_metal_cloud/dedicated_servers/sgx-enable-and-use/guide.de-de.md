---
title: "Intel SGX auf Ihrem Dedicated Server aktivieren"
excerpt: "Erfahren Sie, wie Sie SGX auf Ihrem dedizierten Server aktivieren und den Linux SGX-Software-Stack installieren"
updated: 2025-11-18
---

## Ziel

Die Aktivierung der Intel Software Guard Extensions (SGX) auf Ihrem Server erlaubt es Ihnen, SGX-kompatible Anwendungen auszuführen. Intel SGX bietet erweiterte Hardware- und RAM-Verschlüsselungsfunktionen, um anwendungsspezifische Code- und Datenbereiche zu isolieren.

## Voraussetzungen

- Sie haben einen Dedicated Server kompatibel mit der Option [SGX](/links/bare-metal/sgx) in Ihrem Kunden-Account.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager) oder die [OVHcloud API](/links/api).
- Sie verfügen über die Zugangsdaten, die Sie nach der Installation per E-Mail erhalten haben.
- Ubuntu 24.04 oder equivalent ist auf dem Server installiert.

## In der praktischen Anwendung

### Über das OVHcloud Kundencenter

#### Schritt 1: Anmeldung im OVHcloud Kundencenter

Loggen Sie sich im [OVHcloud Kundencenter](/links/manager) ein, gehen Sie in den Bereich `Bare Metal Cloud`{.action} und wählen Sie dann links im Menü unter **Dedicated Servers** den Server aus, auf dem Sie SGX aktivieren möchten.

#### Schritt 2: SGX aktivieren

Scrollen Sie nach unten zum Bereich "Fortgeschrittene Funktionen" und klicken Sie auf `...`{.action} neben "Sicherheit - Intel SGX (Software Guard Extensions)". Wählen Sie `SGX aktivieren`{.action} aus dem Drop-Down-Menü.

![SGX aktivieren](images/enable_sgx.png){.thumbnail}

Klicken Sie auf der nächsten Seite auf die Schaltfläche `Aktivieren`{.action}.

![SGX aktivieren](images/enable_sgx2.png){.thumbnail}

Sie können entweder SGX mit einer bestimmten Menge reservierten Speichers aktivieren oder SGX aktivieren, indem Sie Ihrem Software-System erlauben, den benötigten Speicher automatisch zu reservieren. Nachdem Sie Ihre Wahl getroffen haben, klicken Sie auf `Bestätigen`{.action}.

![SGX aktivieren](images/manage_sgx.png){.thumbnail}

Es erscheint ein Fenster, um zu bestätigen, dass die Aktivierung von Intel SGX einen Neustart Ihres Servers erfordert.

![SGX aktivieren](images/confirmation-popup_sgx.png){.thumbnail}

> [!warning]
>
> Dies wird dazu führen, dass Ihr Server einmal oder mehrmals neu gestartet wird, abhängig vom Server-Modell.

Fahren Sie mit [Schritt 3](#sgx-softwares) unten fort.

### Über die OVHcloud API

#### Schritt 1: Anmeldung in der API-Konsole

Gehen Sie auf der [OVHcloud API-Seite](/links/api) auf `Login`{.action} in der oberen rechten Ecke. Geben Sie auf der nächsten Seite die Zugangsdaten Ihres OVHcloud Kunden-Accounts ein.

#### Schritt 2: SGX aktivieren

Rufen Sie den Namen Ihres Servers aus der Liste ab, die durch folgenden Aufruf zurückgegeben wird:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server

Um zu überprüfen, ob Ihr Dienst über die SGX-Option verfügt, nutzen Sie folgenden Aufruf: 

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX deaktiviert](images/get-disabled.png){.thumbnail}

Aktivieren Sie SGX unter Verwendung des Servernamens:

> [!warning]
>
> Dies wird dazu führen, dass Ihr Server einmal oder mehrmals neu gestartet wird, abhängig vom Servermodell.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/biosSettings/sgx/configure

![SGX konfigurieren](images/post-configure.png){.thumbnail}

Überprüfen Sie den Fortschritt des Konfigurationstasks, indem Sie diesen Endpunkt mit der *taskId* aufrufen, die vom vorherigen Aufruf zurückgegeben wurde:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/task/{taskId}

![SGX-Konfigurationsaufgabe abrufen](images/get-task.png){.thumbnail}

Sie können bestätigen, dass der Status auf aktiviert gesetzt ist, indem Sie folgenden Aufruf ausführen:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX aktiviert](images/get-enabled.png){.thumbnail}

Fahren Sie mit [Schritt 3](#sgx-softwares) der untenstehenden Anweisungen fort.

### Manuelle Konfiguration im BIOS

#### Schritt 1: Starten Sie eine Remote KVM-Sitzung

Loggen Sie sich im [OVHcloud Kundencenter](/links/manager) ein, gehen Sie in den Bereich `Bare Metal Cloud`{.action} und wählen Sie dann links im Menü unter **Dedicated Servers** den Server aus, auf dem Sie SGX aktivieren möchten.

Starten Sie anschließend eine Remote KVM-Sitzung:

![Starten Sie eine Remote KVM-Sitzung](images/manager.png){.thumbnail}

#### Schritt 2: SGX aktivieren

Starten Sie den Server neu und öffnen Sie das BIOS (meist durch Drücken von `DEL`{.action} oder `F2`{.action}).

Im BIOS wechseln Sie zu `Advanced` > `Processor Configuration`.

Aktivieren Sie die Optionen TME und SGX und konfigurieren Sie die gewünschte PRMRR-Größe:

![SGX aktivieren](images/sgx_bios.png){.thumbnail}

Speichern Sie die Änderungen, indem Sie die Taste `F10`{.action} drücken. Eine Bestätigung wird angezeigt; wählen Sie `Yes`.

Ihr Server wird anschließend neu starten und in Ihr Betriebssystem booten.

Fahren Sie mit [Schritt 3](#sgx-softwares) fort.

### Schritt 3: Installation des SGX-Software-Stacks <a name="sgx-softwares"></a>

Verwenden Sie die folgenden Befehle, um Intels SDK zu installieren, um SGX-Anwendungen entwickeln und ausführen zu können.  

Zunächst installieren Sie diese Dependencies:

```bash
sudo apt update
sudo apt install autoconf automake build-essential cmake debhelper git libcurl4-openssl-dev libprotobuf-dev libssl-dev libtool lsb-release ocaml ocamlbuild protobuf-compiler python-is-python3 reprepro wget perl unzip pkgconf libboost-dev libboost-system-dev libboost-thread-dev lsb-release libsystemd0
```

Laden Sie anschließend den Quellcode herunter und bereiten Sie die Submodule und Binärdateien vor:

```bash
BASE_DIR=/opt/intel
[[ -d $BASE_DIR ]] || sudo mkdir -p $BASE_DIR && sudo chown `whoami` $BASE_DIR
cd $BASE_DIR
 
git clone https://github.com/intel/linux-sgx.git
 
cd linux-sgx
git checkout sgx_2.26
make preparation
```

Installieren Sie das SGX SDK:

```bash
make sdk_install_pkg
$ ./linux/installer/bin/sgx_linux_x64_sdk_2.26.100.0.bin --prefix=$BASE_DIR/
```

### Schritt 4: Testen der Beispielanwendung im Simulator-Modus

Um die Beispielanwendung LocalAttestation im Simulator-Modus zu erstellen und auszuführen:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/sgxsdk/SampleCode/LocalAttestation/
source $BASE_DIR/sgxsdk/environment
 
make clean
SGX_MODE=SIM make
cd bin
./app
succeed to load enclaves.
succeed to establish secure channel.
Succeed to exchange secure message...
Succeed to close Session...
```

### Schritt 5: Erstellen und installieren von Intel SGX PSW

Intel SGX Platform Software (PSW) stellt Software-Bibliotheken bereit, um SGX-Anwendungen im Hardware-Modus auszuführen. Um das lokale Debian-Repository zu erstellen, das die Pakete hostet, führen Sie folgende Befehle aus:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/linux-sgx
make deb_local_repo
```

Erstellen Sie folgende Datei, um das lokale Repository zur System-Repository-Konfiguration hinzuzufügen:

```bash
$ cat /etc/apt/sources.list.d/sgx.sources
Types: deb
URIs: file:/opt/intel/linux-sgx/linux/installer/deb/sgx_debian_local_repo
Suites: noble
Components: main
trusted: yes
```

Installieren Sie anschließend folgende Pakete:

```bash
sudo apt update
sudo apt-get install libsgx-epid libsgx-quote-ex libsgx-dcap-ql
```

### Schritt 6: Testen der Beispielanwendung im Hardware-Modus (optional)

Um die Beispielanwendung LocalAttestation im Hardware-Modus zu erstellen und auszuführen:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/sgxsdk/SampleCode/LocalAttestation/
source $BASE_DIR/sgxsdk/environment
 
make clean
SGX_MODE=HW make
cd bin
./app
succeed to load enclaves.
succeed to establish secure channel.
Succeed to exchange secure message...
Succeed to close Session...
```

## Weiterführende Informationen

Für die weiteren Schritte (Ihre eigene Anwendung entwickeln, sich für die Remote-Bestätigung registrieren, etc.) finden Sie hier weitere nützliche Ressourcen:

- [Intel SGX](https://software.intel.com/en-us/sgx)
- [Intel SGX Attestation services](https://software.intel.com/en-us/sgx/attestation-services)
- [Intel SGX linux-2.26 documentation](https://download.01.org/intel-sgx/sgx-linux/2.26/docs/)
- [github.com/intel/linux-sgx](https://github.com/intel/linux-sgx)
