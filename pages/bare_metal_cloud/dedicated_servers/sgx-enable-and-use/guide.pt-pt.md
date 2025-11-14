---
title: "Como gerir o Intel SGX num servidor dedicado"
excerpt: "Saiba como ativar o SGX no seu servidor dedicado e instalar a pilha de software SGX para Linux"
updated: 2025-11-18
---

## Objetivo

Ativar as Intel Software Guard Extensions (SGX) no seu servidor permite-lhe executar aplicações preparadas para SGX. O Intel SGX oferece funcionalidades avançadas de encriptação de hardware e de memória RAM, para isolar partes de código e dados específicas de cada aplicação.

**Este guia explica como ativar a funcionalidade SGX, no OVHcloud Control Panel ou através da API OVHcloud.**

## Requisitos

- Um servidor dedicado compatível com a [opção SGX](/links/bare-metal/sgx) na sua conta OVHcloud
- Ter acesso a credenciais de início de sessão que recebeu por correio eletrónico após a instalação
- Ter acesso à [Área de Cliente OVHcloud](/links/manager) ou à [API OVHcloud](/links/api)
- Ubuntu 24.04 ou equivalente instalado no servidor

## Instruções

### A partir do OVHcloud Control Panel

#### Passo 1: Iniciar sessão no OVHcloud Control Panel

Inicie sessão no [OVHcloud Control Panel](/links/manager), vá à secção `Bare Metal Cloud`{.action} e selecione o servidor no qual deseja ativar o SGX em **Servidores dedicados** no menu lateral esquerdo.

#### Passo 2: Ativar o SGX

Desça até à caixa "Advanced features" e clique em `...`{.action} ao lado de "Segurança - Intel SGX (Software Guard Extensions)". Selecione `Ativar SGX`{.action} no menu suspenso.

![Ativação do SGX](images/enable_sgx.png){.thumbnail}

Na tela seguinte, clique no botão `Ativar`{.action}.

![Ativação do SGX](images/enable_sgx2.png){.thumbnail}

Pode escolher ativar o SGX com uma quantidade específica de memória reservada ou ativá-lo permitindo que o seu software reserve automaticamente a memória necessária. Após tomar a sua decisão, clique em `Confirmar`{.action}.

![Ativação do SGX](images/manage_sgx.png){.thumbnail}

Aparecerá uma janela pop-up de confirmação. Confirme que compreendeu que a ativação da tecnologia Intel SGX fará com que o seu servidor reinicie.

![Ativação do SGX](images/confirmation-popup_sgx.png){.thumbnail}

> [!warning]
>
> Isto fará com que o seu servidor reinicie uma ou mais vezes, dependendo do modelo do servidor.

Continue com o [Passo 3](#sgx-softwares) das instruções abaixo.

### Usando a API OVHcloud

#### Passo 1: Iniciar sessão na consola da API

Na [página da API OVHcloud](/links/api), clique em `Login`{.action} no canto superior direito. Na página seguinte, introduza as credenciais da sua conta OVHcloud.

#### Passo 2: Ativar o SGX

Obtenha o nome do seu servidor a partir da lista devolvida por esta chamada API:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server

Verifique se o seu serviço tem a opção SGX, chamando: 

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX desativado](images/get-disabled.png){.thumbnail}

Ative o SGX usando o nome do servidor:

> [!warning]
>
> Isto fará com que o seu servidor reinicie uma ou mais vezes, dependendo do modelo do servidor.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/biosSettings/sgx/configure

![Configurar SGX](images/post-configure.png){.thumbnail}

Verifique o progresso da tarefa de configuração chamando este ponto final com o *taskId* devolvido pela chamada anterior:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/task/{taskId}

![Obter tarefa de configuração do SGX](images/get-task.png){.thumbnail}

Pode verificar que o estado está definido como ativado chamando este ponto final:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX ativado](images/get-enabled.png){.thumbnail}

Continue com o [Passo 3](#sgx-softwares) das instruções abaixo.

### Configuração manual no BIOS

#### Passo 1: Iniciar uma sessão Remote KVM

Inicie sessão no [OVHcloud Control Panel](/links/manager), vá à secção `Bare Metal Cloud`{.action} e selecione o servidor no qual deseja ativar o SGX em **Servidores dedicados** no menu lateral esquerdo.

Em seguida, inicie uma sessão Remote KVM:

![Iniciar uma sessão Remote KVM](images/manager.png){.thumbnail}

#### Passo 2: Ativar o SGX

Através do KVM, inicie um reinício do servidor e entre no BIOS (normalmente premindo a tecla `DEL`{.action} ou `F2`{.action}).

No BIOS, vá a `Advanced` > `Processor Configuration`.

Ative as opções TME e SGX e configure o tamanho desejado do PRMRR:

![Ativar SGX](images/sgx_bios.png){.thumbnail}

Guarde as alterações premindo a tecla `F10`{.action}. Aparecerá uma janela pop-up de confirmação, confirme com a opção `Yes`.

O seu servidor reiniciará e arrancará no seu sistema operativo.

Continue com o [Passo 3](#sgx-softwares) das instruções abaixo.

### Passo 3: Instalar a pilha de software SGX <a name="sgx-softwares"></a>

Use os seguintes comandos para instalar o SDK da Intel para poder desenvolver e executar aplicações SGX.  

Primeiro, instale algumas dependências:

```bash
sudo apt update
sudo apt install autoconf automake build-essential cmake debhelper git libcurl4-openssl-dev libprotobuf-dev libssl-dev libtool lsb-release ocaml ocamlbuild protobuf-compiler python-is-python3 reprepro wget perl unzip pkgconf libboost-dev libboost-system-dev libboost-thread-dev lsb-release libsystemd0
```

Em seguida, descarregue o código fonte e prepare os submódulos e as binárias pré-construídas:

```bash
BASE_DIR=/opt/intel
[[ -d $BASE_DIR ]] || sudo mkdir -p $BASE_DIR && sudo chown `whoami` $BASE_DIR
cd $BASE_DIR
 
git clone https://github.com/intel/linux-sgx.git
 
cd linux-sgx
git checkout sgx_2.26
make preparation
```

Construa e instale o SDK SGX:

```bash
make sdk_install_pkg
$ ./linux/installer/bin/sgx_linux_x64_sdk_2.26.100.0.bin --prefix=$BASE_DIR/
```

### Passo 4: Testar a aplicação de exemplo no modo Simulator

Para construir e executar o código de exemplo LocalAttestation no modo Simulator:

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

### Passo 5: Construir e instalar o Intel SGX PSW

O Intel SGX Platform Software (PSW) fornece bibliotecas de software para executar aplicações SGX no modo Hardware. Para construir o repositório local de pacotes Debian que aloja os pacotes, execute os seguintes comandos:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/linux-sgx
make deb_local_repo
```

Crie o seguinte ficheiro para adicionar o repositório local de pacotes Debian à configuração do repositório do sistema:

```bash
$ cat /etc/apt/sources.list.d/sgx.sources
Types: deb
URIs: file:/opt/intel/linux-sgx/linux/installer/deb/sgx_debian_local_repo
Suites: noble
Components: main
trusted: yes
```

Em seguida, instale os seguintes pacotes:

```bash
sudo apt update
sudo apt-get install libsgx-epid libsgx-quote-ex libsgx-dcap-ql
```

### Passo 6: Testar a aplicação de exemplo no modo Hardware (opcional)

Para construir e executar o código de exemplo LocalAttestation no modo Hardware:

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

## Quer saber mais?

Para ir mais longe (desenvolver a sua própria aplicação, registar-se para atestado remoto, etc.), aqui estão alguns recursos úteis:

- [Intel SGX](https://software.intel.com/en-us/sgx)
- [Intel SGX Attestation services](https://software.intel.com/en-us/sgx/attestation-services)
- [Intel SGX linux-2.26 documentation](https://download.01.org/intel-sgx/sgx-linux/2.26/docs/)
- [github.com/intel/linux-sgx](https://github.com/intel/linux-sgx)
