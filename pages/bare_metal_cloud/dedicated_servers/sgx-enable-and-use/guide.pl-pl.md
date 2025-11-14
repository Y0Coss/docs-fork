---
title: "Jak zarządzać Intel SGX na serwerze dedykowanym"
excerpt: "Dowiedz się, jak włączyć SGX na swoim serwerze dedykowanym i zainstalować stos oprogramowania SGX dla systemu Linux"
updated: 2025-11-18
---

## Wprowadzenie

Włączanie Intel Software Guard Extensions (SGX) na Twoim serwerze umożliwia uruchamianie aplikacji gotowych do SGX. Intel SGX oferuje zaawansowane funkcje szyfrowania sprzętu i pamięci RAM, aby izolować fragmenty kodu i danych specyficzne dla każdej aplikacji.

**Ten przewodnik wyjaśnia, jak włączyć funkcję SGX w Panelu klienta OVHcloud lub za pomocą API OVHcloud.**

## Wymagania początkowe

- Serwer dedykowany kompatybilny z [opcją SGX](/links/bare-metal/sgx) w Twoim koncie OVHcloud
- Posiadanie danych do logowania otrzymanych w e-mailu po zakończonej instalacji
- Dostęp do [Panelu klienta OVHcloud](/links/manager) lub [API OVHcloud](/links/api)
- Zainstalowany na serwerze Ubuntu 24.04 lub odpowiednik

## W praktyce

### Z Panelu klienta OVHcloud

#### Krok 1: Logowanie do Panelu klienta OVHcloud

Zaloguj się do [Panelu klienta OVHcloud](/links/manager), przejdź do sekcji `Bare Metal Cloud`{.action} i wybierz serwer, na którym chcesz włączyć SGX z sekcji **Serwery dedykowane** w lewym pasku bocznym.

#### Krok 2: Włączanie SGX

Przewiń w dół do pola "Zaawansowane funkcje" i kliknij `...`{.action} obok "Bezpieczeństwo - Intel SGX (Software Guard Extensions)". Wybierz `Włącz SGX`{.action} z menu rozwijanego.

![Włączanie SGX](images/enable_sgx.png){.thumbnail}

Na kolejnym ekranie kliknij przycisk `Włącz`{.action}.

![Włączanie SGX](images/enable_sgx2.png){.thumbnail}

Możesz wybrać opcję włączenia SGX z określonym ilością zastrzeżonej pamięci lub włączyć ją, pozwalając oprogramowaniu automatycznie rezerwować potrzebną pamięć. Po podjęciu decyzji kliknij `Potwierdź`{.action}.

![Włączanie SGX](images/manage_sgx.png){.thumbnail}

Wyświetli się okno potwierdzenia. Potwierdź, że rozumiesz, że aktywacja technologii Intel SGX spowoduje ponowne uruchomienie serwera.

![Aktywacja SGX](images/confirmation-popup_sgx.png){.thumbnail}

> [!warning]
>
> Spowoduje to ponowne uruchomienie serwera jeden lub kilka razy, w zależności od modelu serwera.

Przejdź do [Kroku 3](#sgx-softwares) poniżej.

### Użycie API OVHcloud

#### Krok 1: Logowanie do konsoli API

Na stronie [API OVHcloud](/links/api) kliknij `Zaloguj`{.action} w prawym górnym rogu. Na kolejnej stronie wprowadź dane logowania do swojego konta OVHcloud.

#### Krok 2: Włączanie SGX

Pobierz nazwę swojego serwera z listy zwróconej przez ten zapytanie:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server

Sprawdź, czy Twoja usługa posiada opcję SGX, wywołując:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX wyłączony](images/get-disabled.png){.thumbnail}

Włącz SGX używając nazwy serwera:

> [!warning]
>
> Spowoduje to ponowne uruchomienie serwera jeden lub kilka razy, w zależności od modelu serwera.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/biosSettings/sgx/configure

![Konfiguracja SGX](images/post-configure.png){.thumbnail}

Sprawdź postęp konfiguracji zadania, wywołując ten punkt końcowy z *taskId* zwróconym przez poprzednie wywołanie:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/task/{taskId}

![Pobierz zadanie konfiguracji SGX](images/get-task.png){.thumbnail}

Możesz sprawdzić, czy status został ustawiony na włączony:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX włączony](images/get-enabled.png){.thumbnail}

Przejdź do [Kroku 3](#sgx-softwares) poniżej.

### Ręczna konfiguracja w BIOS-ie

#### Krok 1: Uruchom sesję Remote KVM

Zaloguj się do [Panelu klienta OVHcloud](/links/manager), przejdź do sekcji `Bare Metal Cloud`{.action} i wybierz serwer, na którym chcesz włączyć SGX z sekcji **Serwery dedykowane** w lewym pasku bocznym.

Następnie uruchom sesję Remote KVM:

![Uruchom sesję Remote KVM](images/manager.png){.thumbnail}

#### Krok 2: Włączanie SGX

Następnie, za pomocą KVM, uruchom ponownie serwer i wejdź do BIOS-u (zazwyczaj naciskając klawisz `DEL`{.action} lub `F2`{.action}).

W BIOS-ie przejdź do `Advanced` > `Processor Configuration`.

Włącz opcje TME i SGX oraz skonfiguruj żądaną wielkość PRMRR:

![Włącz SGX](images/sgx_bios.png){.thumbnail}

Zapisz zmiany, naciskając klawisz `F10`{.action}. Wyświetli się okno potwierdzenia, potwierdź opcją `Yes`.

Twój serwer ponownie uruchomi się i uruchomi się Twoja system operacyjny.

Przejdź do [Kroku 3](#sgx-softwares) poniżej.

### Krok 3: Instalacja stosu oprogramowania SGX <a name="sgx-softwares"></a>

Użyj poniższych poleceń, aby zainstalować zestaw SDK firmy Intel, dzięki czemu będziesz mógł tworzyć i uruchamiać aplikacje SGX.  

Najpierw zainstaluj niektóre zależności:

```bash
sudo apt update
sudo apt install autoconf automake build-essential cmake debhelper git libcurl4-openssl-dev libprotobuf-dev libssl-dev libtool lsb-release ocaml ocamlbuild protobuf-compiler python-is-python3 reprepro wget perl unzip pkgconf libboost-dev libboost-system-dev libboost-thread-dev lsb-release libsystemd0
```

Następnie pobierz kod źródłowy i przygotuj podmoduły oraz binarne wersje gotowe do użycia:

```bash
BASE_DIR=/opt/intel
[[ -d $BASE_DIR ]] || sudo mkdir -p $BASE_DIR && sudo chown `whoami` $BASE_DIR
cd $BASE_DIR
 
git clone https://github.com/intel/linux-sgx.git
 
cd linux-sgx
git checkout sgx_2.26
make preparation
```

Skompiluj i zainstaluj SDK SGX:

```bash
make sdk_install_pkg
$ ./linux/installer/bin/sgx_linux_x64_sdk_2.26.100.0.bin --prefix=$BASE_DIR/
```

### Krok 4: Testowanie przykładowej aplikacji w trybie symulacji

Aby skompilować i uruchomić przykładowy kod LocalAttestation w trybie symulacji:

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

### Krok 5: Kompilacja i instalacja oprogramowania Intel SGX PSW

Oprogramowanie Intel SGX Platform Software (PSW) dostarcza bibliotek oprogramowania, które umożliwia uruchamianie aplikacji SGX w trybie sprzętu. Aby skompilować lokalny repozytorium pakietów Debiana, które hostuje te pakiety, wprowadź poniższe polecenia:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/linux-sgx
make deb_local_repo
```

Utwórz następujący plik, aby dodać lokalne repozytorium Debiana do konfiguracji repozytorium systemowego:

```bash
$ cat /etc/apt/sources.list.d/sgx.sources
Types: deb
URIs: file:/opt/intel/linux-sgx/linux/installer/deb/sgx_debian_local_repo
Suites: noble
Components: main
trusted: yes
```

Następnie zainstaluj poniższe pakiety:

```bash
sudo apt update
sudo apt-get install libsgx-epid libsgx-quote-ex libsgx-dcap-ql
```

### Krok 6: Testowanie przykładowej aplikacji w trybie sprzętu (opcjonalnie)

Aby skompilować i uruchomić przykładowy kod LocalAttestation w trybie sprzętu:

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

## Sprawdź również

Aby przejść dalej (rozwinąć własną aplikację, zarejestrować się do zdalnej attestacji itp.), oto przydatne zasoby:

- [Intel SGX](https://software.intel.com/en-us/sgx)
- [Intel SGX Attestation services](https://software.intel.com/en-us/sgx/attestation-services)
- [Intel SGX linux-2.26 documentation](https://download.01.org/intel-sgx/sgx-linux/2.26/docs/)
- [github.com/intel/linux-sgx](https://github.com/intel/linux-sgx)
