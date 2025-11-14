---
title: "Comment gérer Intel SGX sur un serveur dédié"
excerpt: "Découvrez comment activer SGX sur votre serveur dédié et installer le stack logiciel SGX pour Linux"
updated: 2025-11-18
---

## Objectif

L'activation des Intel Software Guard Extensions (SGX) sur votre serveur vous permet d'exécuter des applications prêtes pour SGX. Intel SGX propose des fonctionnalités avancées de chiffrement matérielle et de la mémoire vive, afin d'isoler les parties de code et de données spécifiques à chaque application.

**Ce guide explique comment activer la fonctionnalité SGX, via l'Espace client OVHcloud ou via l'API OVHcloud.**

## Prérequis

- Un serveur dédié compatible avec l'[option SGX](/links/bare-metal/sgx) dans votre compte OVHcloud
- Accès à l'[Espace client OVHcloud](/links/manager) ou à l'[API OVHcloud](/links/api)
- Identifiants reçus par e-mail après l'installation
- Ubuntu 24.04 ou équivalent installé sur le serveur

## En pratique

### Depuis l'Espace client OVHcloud

#### Étape 1 : Connexion à l'Espace client OVHcloud

Connectez-vous à l'[Espace client OVHcloud](/links/manager), allez à la section `Bare Metal Cloud`{.action} et sélectionnez le serveur sur lequel vous souhaitez activer SGX depuis **Serveurs dédiés** dans la barre latérale de gauche.

#### Étape 2 : Activer SGX

Faites défiler jusqu'à la case "Fonctionnalités avancées" et cliquez sur `...`{.action} à côté de "Sécurité - Intel SGX (Software Guard Extensions)". Sélectionnez `Activer SGX`{.action} dans le menu déroulant.

![Activation SGX](images/enable_sgx.png){.thumbnail}

Sur l'écran suivant, cliquez sur le bouton `Activer`{.action}.

![Activation SGX](images/enable_sgx2.png){.thumbnail}

Vous pouvez choisir d'activer SGX avec une quantité spécifique de mémoire réservée ou l'activer en permettant à votre logiciel de réserver automatiquement la mémoire dont il a besoin. Une fois que vous avez fait votre choix, cliquez sur `Confirmer`{.action}.

![Gestion SGX](images/manage_sgx.png){.thumbnail}

Une fenêtre de confirmation apparaîtra. Veuillez confirmer que vous avez compris que l'activation de la technologie Intel SGX entraînera un redémarrage de votre serveur.

![Activation SGX](images/confirmation-popup_sgx.png){.thumbnail}

> [!warning]
>
> Cela entraînera un ou plusieurs redémarrages de votre serveur, selon le modèle de votre serveur.

Passez à l'[étape 3](#sgx-softwares) des instructions ci-dessous.

### Utilisation de l'API OVHcloud

#### Étape 1 : Connexion à la console API

Sur la [page API OVHcloud](/links/api), cliquez sur `Login`{.action} dans le coin supérieur droit. Sur la page suivante, entrez vos identifiants de compte OVHcloud.

#### Étape 2 : Activer SGX

Récupérez le nom de votre serveur à partir de la liste retournée par cet appel :

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server

Vérifiez que votre service dispose de l'option SGX, en appelant :

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX désactivé](images/get-disabled.png){.thumbnail}

Activez SGX en utilisant le nom du serveur :

> [!warning]
>
> Cela entraînera un ou plusieurs redémarrages de votre serveur, selon le modèle de votre serveur.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/biosSettings/sgx/configure

![Configuration SGX](images/post-configure.png){.thumbnail}

Vérifiez l'avancement de la tâche de configuration en appelant ce point de terminaison avec l'*taskId* retourné par l'appel précédent :

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/task/{taskId}

![Obtenir la tâche de configuration SGX](images/get-task.png){.thumbnail}

Vous pouvez vérifier que l'état est activé :

> [!api]
>
> @api {v1} /dedicated/server GET /dedicated/server/{serviceName}/biosSettings/sgx

![SGX activé](images/get-enabled.png){.thumbnail}

Passez à l'[étape 3](#sgx-softwares) des instructions ci-dessous.

### Configuration manuelle dans le BIOS

#### Étape 1 : Démarrer une session Remote KVM

Connectez-vous à l'[Espace client OVHcloud](/links/manager), allez à la section `Bare Metal Cloud`{.action} et sélectionnez le serveur sur lequel vous souhaitez activer SGX depuis **Serveurs dédiés** dans la barre latérale de gauche.

Ensuite, démarrez une session Remote KVM :

![Démarrer une session Remote KVM](images/manager.png){.thumbnail}

#### Étape 2 : Activer SGX

Ensuite, via le KVM, démarrez un redémarrage du serveur et entrez dans le BIOS (généralement en appuyant sur la touche `DEL`{.action} ou `F2`{.action}).

Dans le BIOS, allez à `Advanced` > `Processor Configuration`.

Activez les options TME et SGX, et configurez la taille PRMRR souhaitée :

![Activer SGX](images/sgx_bios.png){.thumbnail}

Sauvegardez les modifications en appuyant sur la touche `F10`{.action}. Une fenêtre de confirmation apparaîtra, veuillez confirmer avec l'option `Yes`.

Votre serveur redémarrera ensuite et démarrera dans votre système d'exploitation.

Passez à l'[étape 3](#sgx-softwares) des instructions ci-dessous.

### Étape 3 : Installer le stack logiciel SGX <a name="sgx-softwares"></a>

Utilisez les commandes suivantes pour installer le SDK d'Intel afin de pouvoir développer et exécuter des applications SGX.  

Tout d'abord, installez quelques dépendances :

```bash
sudo apt update
sudo apt install autoconf automake build-essential cmake debhelper git libcurl4-openssl-dev libprotobuf-dev libssl-dev libtool lsb-release ocaml ocamlbuild protobuf-compiler python-is-python3 reprepro wget perl unzip pkgconf libboost-dev libboost-system-dev libboost-thread-dev lsb-release libsystemd0
```

Ensuite, téléchargez le code source et préparez les sous-modules et les binaires prêts à l'emploi :

```bash
BASE_DIR=/opt/intel
[[ -d $BASE_DIR ]] || sudo mkdir -p $BASE_DIR && sudo chown `whoami` $BASE_DIR
cd $BASE_DIR
 
git clone https://github.com/intel/linux-sgx.git
 
cd linux-sgx
git checkout sgx_2.26
make preparation
```

Construisez et installez le SDK SGX :

```bash
make sdk_install_pkg
$ ./linux/installer/bin/sgx_linux_x64_sdk_2.26.100.0.bin --prefix=$BASE_DIR/
```

### Étape 4 : Tester l'application d'exemple en mode simulateur

Pour construire et exécuter le code d'exemple LocalAttestation en mode simulateur :

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

### Étape 5 : Construire et installer le PSW Intel SGX

Le logiciel Intel SGX Platform Software (PSW) fournit des bibliothèques logicielles pour exécuter des applications SGX en mode matériel. Pour construire le dépôt local de paquets Debian hébergeant les paquets, entrez les commandes suivantes :

```bash
BASE_DIR=/opt/intel
cd $BASE_DIR/linux-sgx
make deb_local_repo
```

Créez le fichier suivant pour ajouter le dépôt local de paquets Debian au système de configuration des dépôts :

```bash
$ cat /etc/apt/sources.list.d/sgx.sources
Types: deb
URIs: file:/opt/intel/linux-sgx/linux/installer/deb/sgx_debian_local_repo
Suites: noble
Components: main
trusted: yes
```

Ensuite, installez les paquets suivants :

```bash
sudo apt update
sudo apt-get install libsgx-epid libsgx-quote-ex libsgx-dcap-ql
```

### Étape 6 : Tester l'application d'exemple en mode matériel (optionnel)

Pour construire et exécuter le code d'exemple LocalAttestation en mode matériel :

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

## Aller plus loin

Pour aller plus loin (développer votre propre application, vous inscrire à l'attestation distante, etc.), voici quelques ressources utiles :

- [Intel SGX](https://software.intel.com/en-us/sgx)
- [Intel SGX Attestation services](https://software.intel.com/en-us/sgx/attestation-services)
- [Intel SGX linux-2.26 documentation](https://download.01.org/intel-sgx/sgx-linux/2.26/docs/)
- [github.com/intel/linux-sgx](https://github.com/intel/linux-sgx)
