---
title: "Installer N8N sur un VPS OVHcloud"
excerpt: "Apprenez à héberger la plateforme d’automatisation N8N sur un VPS OVHcloud à l’aide de Docker et Traefik"
updated: 2025-06-11
---

## Objectif

Ce guide vous explique comment installer et exécuter [n8n](https://n8n.io), une plateforme open source d’automatisation de workflows, sur un VPS OVHcloud. L’installation s’appuie sur [Docker](https://www.docker.com/), avec le serveur [Traefik](https://doc.traefik.io/traefik/ ) pour gérer automatiquement les certificats SSL.

## Prérequis

- Disposer d'un [VPS](https://www.ovhcloud.com/fr/vps/) fonctionnel (Debian 11 ou supérieur recommandé)
- Disposer d'un nom de domaine
- Disposer d'un accès administrateur (sudo) via SSH à votre serveur

## En pratique

### Se connecter à votre VPS

Ouvrez un terminal et connectez-vous à votre VPS avec la commande suivante (en remplaçant `IP_DU_VPS` par la véritable IP) :

```bash
ssh <user>@IP_VPS
```

### Installer Docker et Docker Compose

Pour déployer N8N via Docker sur un VPS OVHcloud, Docker et Docker Compose doivent être installés. Cette méthode est compatible avec la majorité des distributions proposées par OVHcloud (Debian 11, Debian 12, Ubuntu 22.04...).

#### Étape 1 - Mettez le système à jour

```bash
sudo apt update && sudo apt upgrade -y
```

#### Étape 2 - Ajouter la clé GPG officielle de Docker

```bash
sudo apt install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

#### Étape 3 - Ajouter le dépôt Docker

Pour Debian (version 11 et 12) :

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Pour Ubuntu (version égale ou supérieure à 22.04) :

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### Étape 4 - Installer Docker Engine et Docker Compose Plugin

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### Étape 5 - Vérifier que Docker et Docker Compose fonctionnent

```bash
docker --version
docker compose version
```

### Préparer la configuration Traefik + N8N

Créez un dossier de projet où résidera la stack Docker :

```bash
mkdir n8n-traefik && cd n8n-traefik
```

### Créer les fichiers de configuration.

#### Fichier .env

Ce fichier vous permet de définir les variables réutilisées dans le fichier docker-compose.yml.

Créez le fichier :

```bash
nano .env
```

Collez-y le contenu suivant :

```console
DOMAIN_NAME=exemple.com
SUBDOMAIN=n8n
EMAIL=admin@exemple.com
```

Remplacez `exemple.com` par votre véritable nom de domaine et `admin@exemple.com` par l'e-mail de votre choix.

> [!warning]
>
> Si vous ne possédez pas encore de nom de domaine, commandez-en un sur notre [site web](https://www.ovhcloud.com/fr/domains/).

#### Fichier docker-compose.yml

Ce fichier contient la définition des services N8N et Traefik. Il configure notamment :

- Le reverse proxy et la gestion SSL avec Traefik.
- L’authentification de base pour accéder à N8N.


Créez le fichier :

```bash
nano docker-compose.yml
```

Collez le contenu suivant :

```console
services:
  traefik:
    image: traefik:v2.11
    container_name: traefik
    restart: always
    command:
      - "--api.insecure=true"
      - "--providers.docker=true"
      - "--entrypoints.web.address=:80"
      - "--entrypoints.websecure.address=:443"
      - "--certificatesresolvers.myresolver.acme.httpchallenge=true"
      - "--certificatesresolvers.myresolver.acme.httpchallenge.entrypoint=web"
      - "--certificatesresolvers.myresolver.acme.email=${EMAIL}"
      - "--certificatesresolvers.myresolver.acme.storage=/letsencrypt/acme.json"
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock:ro"
      - "./letsencrypt:/letsencrypt"
    labels:
      - "traefik.http.routers.http-catch.rule=Host(`${SUBDOMAIN}.${DOMAIN_NAME}`)"
      - "traefik.http.routers.http-catch.entrypoints=web"
      - "traefik.http.routers.http-catch.middlewares=redirect-to-https"
      - "traefik.http.middlewares.redirect-to-https.redirectscheme.scheme=https"

  n8n:
    image: n8nio/n8n
    container_name: n8n
    restart: always
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=admin123
      - N8N_HOST=${SUBDOMAIN}.${DOMAIN_NAME}
      - WEBHOOK_URL=https://${SUBDOMAIN}.${DOMAIN_NAME}/
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.n8n.rule=Host(`${SUBDOMAIN}.${DOMAIN_NAME}`)"
      - "traefik.http.routers.n8n.entrypoints=websecure"
      - "traefik.http.routers.n8n.tls.certresolver=myresolver"
      - "traefik.http.services.n8n.loadbalancer.server.port=5678"
    volumes:
      - n8n_data:/home/node/.n8n

volumes:
  n8n_data:
```

> [!warning]
>
> Par défaut, l’utilisateur et le mot de passe sont définis sur admin / admin123. Cette méthode n’est pas activée dans toutes les versions de N8N. Si vous souhaitez l’utiliser malgré tout, pensez à modifier ces valeurs dans le fichier docker-compose.yml avant de lancer la stack, et utilisez un mot de passe fort.

### Préparer le dossier des certificats SSL

Traefik stocke les certificats générés par Let's Encrypt dans un fichier nommé acme.json. Ce fichier doit exister avant le lancement et avoir des permissions strictes.

Créez le dossier :

```bash
mkdir letsencrypt
```

Créez le fichier vide :

```bash
touch letsencrypt/acme.json
chmod 600 letsencrypt/acme.json
```

### Démarrer les services

Lancez la stack avec Docker Compose :

```bash
docker compose up -d
```

### Configuration DNS

Assurez-vous que votre sous-domaine (ex : n8n.exemple.com) pointe bien vers l’adresse IP de votre VPS dans la zone DNS. Pour plus de détails, consultez notre guide « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit){.external} ».

### Accéder à l’interface N8N

Accédez à N8N dans un navigateur via l'URL `https://n8n.exemple.com/`. Remplacez `n8n.exemple.com` par le domaine réel que vous avez défini. La page suivante s'affiche.

![Install N8N VPS](images/setup_n8n.png){.thumbnail}

Une fois la page chargée, vous serez invité à créer le premier utilisateur administrateur de votre instance N8N via le formulaire de configuration.

### Conclusion

Vous disposez désormais d’une instance N8N opérationnelle et sécurisée sur votre VPS OVHcloud, avec une gestion automatique des certificats SSL grâce à Traefik. Pour aller plus loin, consultez la [documentation officielle](https://docs.n8n.io/) de N8N pour créer vos premiers workflows.

## Aller plus loin

[Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit){.external}

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr-ca/directory/)

Échangez avec notre [communauté d'utilisateurs](/links/community).
