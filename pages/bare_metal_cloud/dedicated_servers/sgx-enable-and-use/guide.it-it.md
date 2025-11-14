---
title: "Come gestire Intel SGX su un server dedicato"
excerpt: "Scopri come abilitare SGX sul tuo server dedicato e installare il software stack Linux SGX"
updated: 2025-11-18
---

## Obiettivo

Abilitare Intel Software Guard Extensions (SGX) sul tuo server ti permette di eseguire applicazioni pronte per SGX. Intel SGX fornisce funzionalità avanzate di crittografia hardware e RAM, al fine di isolare parti di codice e dati specifici per ciascuna applicazione.

**Questa guida spiega come abilitare la funzionalità SGX, tramite lo Spazio Cliente OVHcloud o tramite l'API OVHcloud.**

## Prerequisiti

- Un server dedicato compatibile con l'[opzione SGX](/links/bare-metal/sgx) nel tuo account OVHcloud
- Disporre delle credenziali di accesso ricevute via email in seguito all’installazione
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager) o all’[API OVHcloud](/links/api)
- Ubuntu 24.04 o equivalente installato sul server

## Procedura

### Dallo Spazio Cliente OVHcloud

#### Passo 1: Accedere allo Spazio Cliente OVHcloud

Accedi allo [Spazio Cliente OVHcloud](/links/manager), vai alla sezione `Bare Metal Cloud`{.action} e seleziona il server su cui desideri abilitare SGX da **Server dedicati** nel menu laterale sinistro.

#### Passo 2: Abilitare SGX

Scorri verso il basso fino alla casella "Advanced features" e clicca su `...`{.action} accanto a "Security - Intel SGX (Software Guard Extensions)". Seleziona `Enable SGX`{.action} dal menu a discesa.

![Abilitazione SGX](images/enable_sgx.png){.thumbnail}

Nello schermo successivo, clicca sul pulsante `Attiva`{.action}.

![Abilitazione SGX](images/enable_sgx2.png){.thumbnail}

Puoi scegliere di abilitare SGX con una quantità specifica di memoria riservata oppure abilitarlo permettendo al tuo software di riservare automaticamente la memoria necessaria. Una volta effettuata la scelta, clicca su `Conferma`{.action}.

![Abilitazione SGX](images/manage_sgx.png){.thumbnail}

Verrà visualizzata una finestra di conferma. Conferma di aver compreso che l'attivazione della tecnologia Intel SGX farà riavviare il tuo server.

![Attivazione SGX](images/confirmation-popup_sgx.png){.thumbnail}

> [!warning]
>
> Questo farà riavviare il tuo server una o più volte, a seconda del modello del server.

Procedi con il [Passo 3](#sgx-softwares) delle istruzioni qui sotto.

### Utilizzo dell'API OVHcloud

#### Passo 1: Accedere alla console API

Sulla pagina [OVHcloud API](/links/api) clicca su `Login`{.action} nell'angolo in alto a destra. Nella pagina successiva, inserisci le credenziali del tuo account OVHcloud.

#### Passo 2: Abilitare SGX

Recupera il nome del tuo server dalla lista restituita da questa chiamata API:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server

Verifica che il tuo servizio abbia l'opzione SGX, effettuando la seguente chiamata API: 

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX disabilitato](images/get-disabled.png){.thumbnail}

Abilita SGX utilizzando il nome del server:

> [!warning]
>
> Questo farà riavviare il tuo server una o più volte, a seconda del modello del server.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/biosSettings/sgx/configure

![Configura SGX](images/post-configure.png){.thumbnail}

Controlla lo stato dell'attività di configurazione chiamando questo endpoint con l'*taskId* restituito dalla chiamata precedente:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/task/{taskId}

![Ottieni attività di configurazione SGX](images/get-task.png){.thumbnail}

Puoi verificare che lo stato sia impostato su abilitato effettuando la seguente chiamata API:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX abilitato](images/get-enabled.png){.thumbnail}

Procedi con il [Passo 3](#sgx-softwares) delle istruzioni qui sotto.

### Configurazione manuale nel BIOS

#### Passo 1: Avviare una sessione Remote KVM

Accedi allo [Spazio Cliente OVHcloud](/links/manager), vai alla sezione `Bare Metal Cloud`{.action} e seleziona il server su cui desideri abilitare SGX da **Server dedicati** nel menu laterale sinistro.

Quindi, avvia una sessione Remote KVM:

![Avvia una sessione Remote KVM](images/manager.png){.thumbnail}

#### Passo 2: Abilitare SGX

Quindi, tramite il KVM, avvia un riavvio del server e accedi al BIOS (di norma premendo il tasto `DEL`{.action} o `F2`{.action}).

Nel BIOS, vai a `Advanced` > `Processor Configuration`.

Abilita le opzioni TME e SGX e configura la dimensione desiderata di PRMRR:

![Abilita SGX](images/sgx_bios.png){.thumbnail}

Salva le modifiche premendo il tasto `F10`{.action}. Verrà visualizzata una finestra di conferma, conferma con l'opzione `Yes`.

Il tuo server verrà quindi riavviato e avvierà il tuo sistema operativo.

Procedi con il [Passo 3](#sgx-softwares) delle istruzioni qui sotto.

### Passo 3: Installare il software stack SGX <a name="sgx-softwares"></a>

Utilizza i seguenti comandi per installare l'SDK di Intel in modo da poter sviluppare ed eseguire applicazioni SGX.  

Prima, installa alcune dipendenze:

```bash
sudo apt update
sudo apt install autoconf automake build-essential cmake debhelper git libcurl4-openssl-dev libprotobuf-dev libssl-dev libtool lsb-release ocaml ocamlbuild protobuf-compiler python-is-python3 reprepro wget perl unzip pkgconf libboost-dev libboost-system-dev libboost-thread-dev lsb-release libsystemd0
```

Quindi, scarica il codice sorgente e prepara i sottomoduli e i binari precompilati:

```bash
BASE_DIR=/opt/intel
[[ -d $BASE_DIR ]] || sudo mkdir -p $BASE_DIR && sudo chown `whoami` $BASE_DIR
cd $BASE_DIR
 
git clone https://github.com/intel/linux-sgx.git
 
cd linux-sgx
git checkout sgx_2.26
make preparation
```

Compila e installa l'SDK SGX:

```bash
make sdk_install_pkg
$ ./linux/installer/bin/sgx_linux_x64_sdk_2.26.100.0.bin --prefix=$BASE_DIR/
```

### Passo 4: Test dell'applicazione di esempio in modalità Simulator

Per compilare ed eseguire il codice di esempio LocalAttestation in modalità Simulator:

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

### Passo 5: Compilare e installare Intel SGX PSW

Intel SGX Platform Software (PSW) fornisce librerie software per eseguire applicazioni SGX in modalità Hardware. Per compilare il repository locale Debian che ospita i pacchetti, esegui i seguenti comandi:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/linux-sgx
make deb_local_repo
```

Crea il seguente file per aggiungere il repository Debian locale alla configurazione del repository di sistema:

```bash
$ cat /etc/apt/sources.list.d/sgx.sources
Types: deb
URIs: file:/opt/intel/linux-sgx/linux/installer/deb/sgx_debian_local_repo
Suites: noble
Components: main
trusted: yes
```

Quindi, installa i seguenti pacchetti:

```bash
sudo apt update
sudo apt-get install libsgx-epid libsgx-quote-ex libsgx-dcap-ql
```

### Passo 6: Test dell'applicazione di esempio in modalità Hardware (opzionale)

Per compilare ed eseguire il codice di esempio LocalAttestation in modalità Hardware:

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

## Per saperne di più

Per andare oltre (sviluppare la tua applicazione, registrarti per l'attestazione remota, ecc.), ecco alcune risorse utili:

- [Intel SGX](https://software.intel.com/en-us/sgx)
- [Intel SGX Attestation services](https://software.intel.com/en-us/sgx/attestation-services)
- [Intel SGX linux-2.26 documentation](https://download.01.org/intel-sgx/sgx-linux/2.26/docs/)
- [github.com/intel/linux-sgx](https://github.com/intel/linux-sgx)
