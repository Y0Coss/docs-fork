---
title: "How to manage Intel SGX on a dedicated server"
excerpt: "Find out how to enable SGX on your dedicated server and install the Linux SGX software stack"
updated: 2025-11-18
---

## Objective

Enabling Intel Software Guard Extensions (SGX) on your server allows you to run SGX-ready applications. Intel SGX delivers advanced hardware and RAM security encryption features, in order to isolate parts of code and data that are specific to each application.

**This guide explains how to enable the SGX feature, in the OVHcloud Control Panel or via the OVHcloud API.**

## Requirements

- A dedicated server compatible with the [SGX option](/links/bare-metal/sgx) in your OVHcloud account
- Access to the [OVHcloud Control Panel](/links/manager) or the [OVHcloud API](/links/api)
- Login credentials received via email after the installation
- Ubuntu 24.04 or equivalent installed on the server

## Instructions

### From the OVHcloud Control Panel

#### Step 1: Logging in to the OVHcloud Control Panel

Log in to the [OVHcloud Control Panel](/links/manager), go to the `Bare Metal Cloud`{.action} section and then select the server on which you wish to enable SGX from **Dedicated Servers** in the left-hand sidebar.

#### Step 2: Enabling SGX

Scroll down to the "Advanced features" box and click on `...`{.action} next to "Security - Intel SGX (Software Guard Extensions)". Select `Enable SGX`{.action} from the drop-down menu.

![SGX enabling](images/enable_sgx.png){.thumbnail}

On the following screen, click the `Enable`{.action} button.

![SGX enabling](images/enable_sgx2.png){.thumbnail}

You can either choose to enable SGX with a specific amount of reserved memory or enable it by allowing your software to automatically reserve the memory it needs. Once you have made your choice, click `Confirm`{.action}.

![SGX enabling](images/manage_sgx.png){.thumbnail}

A confirmation pop-up will appear. Please confirm you have understood that activating Intel SGX technology will make your server reboot.

![activation SGX](images/confirmation-popup_sgx.png){.thumbnail}

> [!warning]
>
> This will cause your server to reboot once or several times, depending on your server model.

Continue with [Step 3](#sgx-softwares) of the instructions below.

### Using the OVHcloud API

#### Step 1: Logging in to the API console

On the [OVHcloud API page](/links/api) click on `Login`{.action} in the top-right corner. On the following page, enter the credentials of your OVHcloud account.

#### Step 2: Enabling SGX

Retrieve the name of your server from the list returned from this call:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server

Verify that your service has the SGX option, by calling: 

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX disabled](images/get-disabled.png){.thumbnail}

Enable SGX using the server name:

> [!warning]
>
> This will cause your server to reboot once or several times, depending on your server model.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/biosSettings/sgx/configure

![Configure SGX](images/post-configure.png){.thumbnail}

Check the progress of the configuration task by calling this endpoint with the *taskId* returned by the previous call:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/task/{taskId}

![Get SGX configuration task](images/get-task.png){.thumbnail}

You can verify that the status is set to enabled:

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX enabled](images/get-enabled.png){.thumbnail}

Continue with [Step 3](#sgx-softwares) of the instructions below.

### Manual configuration in the BIOS

#### Step 1: Start a Remote KVM session

Log in to the [OVHcloud Control Panel](/links/manager), go to the `Bare Metal Cloud`{.action} section and then select the server on which you wish to enable SGX from **Dedicated Servers** in the left-hand sidebar.

Then, start a Remote KVM session:

![Start a Remote KVM session](images/manager.png){.thumbnail}

#### Step 2: Enabling SGX

Then, through the KVM, initiate a server reboot and enter the BIOS (usually by pressing the `DEL`{.action} or `F2`{.action} key).

In the BIOS, go to `Advanced` > `Processor Configuration`.

Enable TME and SGX options, and configure the desired PRMRR size:

![Enable SGX](images/sgx_bios.png){.thumbnail}

Save the changes by pressing the `F10`{.action} key. A confirmation pop-up will appear, please confirm with the `Yes` option.

Your server will then restart and boot into your OS.

Continue with [Step 3](#sgx-softwares) of the instructions below.

### Step 3: Installing the SGX software stack <a name="sgx-softwares"></a>

Use the following commands to install Intel's SDK to be able to develop and run SGX applications.  

First, install some dependencies:

```bash
sudo apt update
sudo apt install autoconf automake build-essential cmake debhelper git libcurl4-openssl-dev libprotobuf-dev libssl-dev libtool lsb-release ocaml ocamlbuild protobuf-compiler python-is-python3 reprepro wget perl unzip pkgconf libboost-dev libboost-system-dev libboost-thread-dev lsb-release libsystemd0
```

Then, download the source code and prepare the submodules and prebuilt binaries:

```bash
BASE_DIR=/opt/intel
[[ -d $BASE_DIR ]] || sudo mkdir -p $BASE_DIR && sudo chown `whoami` $BASE_DIR
cd $BASE_DIR
 
git clone https://github.com/intel/linux-sgx.git
 
cd linux-sgx
git checkout sgx_2.26
make preparation
```

Build and install SGX SDK:

```bash
make sdk_install_pkg
$ ./linux/installer/bin/sgx_linux_x64_sdk_2.26.100.0.bin --prefix=$BASE_DIR/
```

### Step 4: Test sample application in Simulator mode

To build and run LocalAttestation sample code in Simulator mode:

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

### Step 5: Build and install Intel SGX PSW

Intel SGX Platform Software (PSW) provides software libraries to run SGX applications in Hardware mode. To build the local Debian package repository hosting the packages enter the following commands:

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/linux-sgx
make deb_local_repo
```

Create the following file to add the local Debian package repository to the system repository configuration:

```bash
$ cat /etc/apt/sources.list.d/sgx.sources
Types: deb
URIs: file:/opt/intel/linux-sgx/linux/installer/deb/sgx_debian_local_repo
Suites: noble
Components: main
trusted: yes
```

Then, install the following packages:

```bash
sudo apt update
sudo apt-get install libsgx-epid libsgx-quote-ex libsgx-dcap-ql
```

### Step 6: Test sample application in Hardware mode (optional)

To build and run LocalAttestation sample code in Hardware mode:

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

## Go further

To go further (develop your own application, register for remote attestation, etc.), here are some useful resources:

- [Intel SGX](https://software.intel.com/en-us/sgx)
- [Intel SGX Attestation services](https://software.intel.com/en-us/sgx/attestation-services)
- [Intel SGX linux-2.26 documentation](https://download.01.org/intel-sgx/sgx-linux/2.26/docs/)
- [github.com/intel/linux-sgx](https://github.com/intel/linux-sgx)
