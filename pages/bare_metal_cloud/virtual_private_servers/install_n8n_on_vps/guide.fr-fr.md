---
title: "Installer N8N sur un VPS OVHcloud"
excerpt: "Apprenez à héberger la plateforme d’automatisation N8N sur un VPS OVHcloud à l’aide de Docker et Caddy"
updated: 2025-06-03
---

## Objectif

Ce guide vous explique comment installer et exécuter [n8n](https://n8n.io), une plateforme open source d’automatisation de workflows, sur un VPS OVHcloud. L’installation s’appuie sur [Docker](https://www.docker.com/), avec le serveur [Caddy](https://caddyserver.com/) pour gérer automatiquement les certificats SSL.

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

Pour Ubuntu (version égale ou suppérieure à 22.04) :

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

### Récupérer le dépôt de configuration N8N + Caddy

Clonez le dépôt Git officiel contenant une stack Docker prête à l’emploi :

```bash
git clone https://github.com/n8n-io/n8n-docker-caddy.git
cd n8n-docker-caddy
```

> [!primary]
>
> Dans ce guide, le dossier cloné est aussi appelé dossier de données (`DATA_FOLDER`).

Créez les volumes nécessaires :

```bash
sudo docker volume create caddy_data
sudo docker volume create n8n_data
```

### Ouvrir les ports nécessaires

Pour que votre VPS accepte les connexions web (HTTP et HTTPS), ouvrez les ports 80 et 443 via UFW (le pare-feu par défaut sur Debian/Ubuntu) :

```bash
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw allow 443
```

> [!primary]
>
> Si UFW n’est pas installé, vous pouvez l’installer et l’activer avec : `sudo apt install ufw -y`

Activez le pare-feu :

```bash
sudo ufw enable
```

Vérifiez l’état du pare-feu :

```bash
sudo ufw status
```

Vous devez voir une sortie similaire à ceci :

Status: active

To                         Action      From
--                         ------      ----
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
OpenSSH                    ALLOW       Anywhere
80 (v6)                    ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)
OpenSSH (v6)               ALLOW       Anywhere (v6)

### Configurer le fichier `.env`

Le fichier `.env` permet de définir les paramètres d’environnement nécessaires à N8N et Caddy. Pour le créer :

```bash
nano .env
```

```console
DATA_FOLDER=/home/debian/n8n-docker-caddy
DOMAIN_NAME=exemple.com
SUBDOMAIN=n8n
GENERIC_TIMEZONE=Europe/Paris
SSL_EMAIL=mon-adresse@email.com
```

Explications :

- DATA_FOLDER : chemin absolu vers le dossier où vous avez cloné le dépôt Git (dossier de données).
- DOMAIN_NAME : nom de domaine principal (déjà configuré dans votre zone DNS).
- SUBDOMAIN : sous-domaine pointant vers votre VPS (ex : `n8n.exemple.com`).
- GENERIC_TIMEZONE : fuseau horaire utilisé par défaut (important pour les automatisations).
- SSL_EMAIL : e-mail utilisé pour générer le certificat SSL via Let's Encrypt.

Assurez-vous que votre sous-domaine pointe bien vers l’adresse IP de votre VPS dans la zone DNS. Pour plus de détails, consultez notre guide « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit){.external} ».

Redéployez ensuite la stack Docker pour que la configuration soit prise en compte :

```bash
sudo docker compose down
sudo docker compose up -d
```

### Définir le domaine dans Caddy

Vous avez deux manières de définir le domaine dans le fichier `Caddyfile` :

- La modification manuelle est simple et rapide si vous ne comptez faire qu'une seule installation ou modification.
- La génération dynamique via un script est recommandée si vous gérez plusieurs environnements (développement, production, etc.), ou si vous souhaitez automatiser les déploiements à partir d’un fichier `.env`. Cela permet d’éviter les erreurs manuelles et de centraliser la configuration.

#### Option 1 : Modifier manuellement le fichier `Caddyfile`

Ouvrez le fichier CaddyFile :

```bash
nano caddy_config/Caddyfile
```

Remplacez le contenu du fichier par :

```console
n8n.<domain>.com {
    reverse_proxy n8n:5678 {
        flush_interval -1
    }
}
```

Remplacez `<domain>` par votre véritable nom de domaine.

Relancez Docker :

```bash
sudo docker compose down
sudo docker compose up -d
```

#### Option 2 : Générer dynamiquement le fichier `Caddyfile`

Créez un fichier à la racine de votre dossier de données (`n8n-docker-caddy` dans notre exemple) :

```bash
nano generate-caddyfile.sh
```

Collez le contenu suivant :

```console
#!/bin/bash

# Charge les variables depuis le fichier .env
set -a
source .env
set +a

# Génére dynamiquement le fichier Caddyfile
cat <<EOF > caddy_config/Caddyfile
${SUBDOMAIN}.${DOMAIN_NAME} {
  reverse_proxy n8n:5678 {
    flush_interval -1
  }
}
EOF

echo "Fichier Caddyfile généré avec succès."
```

Rendez le script exécutable :

```bash
chmod +x generate-caddyfile.sh
```

Puis lancez-le :

```bash
./generate-caddyfile.sh
```

Relancez Docker :

```bash
sudo docker compose down
sudo docker compose up -d
```

> [!primary]
>
> Le fichier `caddy_config/Caddyfile` sera écrasé à chaque exécution du script. Ne le mofifiez pas manuellement si vous choisissez cette option. À la place, ajoutez un commentaire du type : `# Ce fichier est généré automatiquement par le script generate-caddyfile.sh`.

#### Accéder à N8N

Accédez à N8N dans un navigateur via l'URL `https://n8n.exemple.com/`. Remplacez `n8n.exemple.com` par le domaine réel que vous avez défini. La page suivante s'affiche.

![Install N8N VPS](images/setup_n8n.png){.thumbnail}

Une fois la page chargée, vous serez invité à créer le premier utilisateur administrateur de votre instance N8N via le formulaire de configuration.

### Conclusion

Vous disposez désormais d’une instance N8N opérationnelle et sécurisée sur votre VPS OVHcloud, avec une gestion automatique des certificats SSL grâce à Caddy. Pour aller plus loin, consultez la [documentation officielle](https://docs.n8n.io/) de N8N pour créer vos premiers workflows.

## Aller plus loin

[Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit){.external}

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr-ca/directory/)

Échangez avec notre [communauté d'utilisateurs](/links/community).
