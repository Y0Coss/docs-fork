---
title: "Importer un site Lovable.dev sur un VPS OVHcloud"
excerpt: "Apprenez comment héberger un site généré par Lovable.dev sur votre VPS OVHcloud"
updated: 2025-06-16
---

## Objectif

[Lovable.dev](https://lovable.dev) est un outils qui permet de générer des sites web à partir de prompts. Ce guide vous explique comment importer et publier un site web généré via Lovable sur un **hébergement mutualisé OVHcloud**.  

## Prérequis

- Disposer d'une offre [VPS OVHcloud](https://www.ovhcloud.com/fr/vps/)
- Disposer d'un accès administrateur (sudo) via SSH à votre serveur
- Posséder un compte sur [Lovable.dev](https://lovable.dev)

## En pratique

### Étape 1 : Générer votre site web sur Lovable.dev

1. Rendez-vous sur [https://lovable.dev](https://lovable.dev).
2. Créez un compte si ce n'est pas déjà fait.
3. Entrez votre prompt pour générer votre site web.

### Étape 2 : Exporter votre site web via GitHub et récupérez-le

Une fois votre site web généré par Lovable, exportez-le via GitHub. Dans l'interface principale de Lovable.dev, cliquez en haut à droite sur l'icône de Github (`Sync your project to GitHub`).

![hosting](images/synch_project_github_button.png){.thumbnail}

Pour connecter votre compte Lovable à GitHub, suivez la documentation officielle de [Lovable.dev](https://lovable.dev/integrations/github).

Une fois le processus terminé, un nouveau dépôt contenant le code de votre site web est présent dans votre compte GitHub.

Depuis le dépôt GitHub contenant le code de votre site web, effectuez les actions suivantes :

- Cliquez sur `Code`{.action} puis sur `Download ZIP`{.action}
- Cela télécharge un fichier `.zip` contenant votre projet
- Décompressez-le.

### Étape 3 : Envoyer l’archive sur le VPS

Dans votre terminal (à l’emplacement où se trouve le fichier .zip), utilisez cette commande :

```bash
scp mon_site.zip <utilisateur>@<IP_VPS>:~
```

Remplacez :

- `mon_site.zip` par le nom du fichier téléchargé depuis lovable
- `<utilisateur>` par votre nom d'utilisateur root (ex: debian, root, etc.)
- `<IP_VPS>` par l'adresse IP publique ou le nom DNS de votre VPS

`~` fait référence au dossier personnel de l'utilisateur.

### Étape 4 : Installer Node.js et les outils nécessaires

Connectez-vous en SSH à votre VPS :

```bash
ssh <utilisateur>@<IP_VPS>
```

Pour construire un site web Lovable, vous devez compiler le projet React en version optimisée à l’aide de la commande `npm run build`. Pour cela, il vous faut les éléments suivants sur le VPS :

- `Node.js` : L’environnement JavaScript nécessaire à l’exécution de React.
- `npm` : Le gestionnaire de paquets JavaScript qui installe les dépendances du projet.
- `curl` : Permet de télécharger le script d’installation de Node.js.
- `unzip` : Sert à extraire l’archive `.zip` du site exporté depuis Lovable.

Exécutez ces commandes :

```bash
sudo apt update
sudo apt install curl unzip -y
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo bash -
sudo apt install -y nodejs
```

Vérifiez l'installation :

```bash
node -v
npm -v
```

### Étape 5 : Décompresser et builder votre site web

Décompressez l'archive `.zip` dans un dossier de destination (ex: `lovable-src`):

```bash
unzip mon_site.zip -d lovable-src
```

Entrez dans le dossier de destination :

```bash
cd lovable-src/mon_site
```

Installez les dépendances nécessaires :

```bash
npm install
```

Cela va installer toutes les bibliothèques React/Lovable définies dans le fichier package.json.

Générez les fichiers optimisés (build de production) :

```bash
npm run build
```

Cela crée un dossier `dist/` contenant les fichiers HTML, CSS et JS minifiés.

### Étape 6 : Déployer le site avec NGINX

Créez le dossier public :

```bash
sudo mkdir -p /var/www/lovable
sudo cp -r dist/* /var/www/lovable/
```

### Étape 7 : Installer et configurer NGINX

