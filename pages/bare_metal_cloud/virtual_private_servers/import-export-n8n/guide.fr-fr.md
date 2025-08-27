---

title: "Migrer une configuration n8n entre deux VPS (OVHcloud ou autres)"
excerpt: "Découvrez comment exporter et importer une configuration n8n complète (workflows et identifiants) d’un VPS externe vers un VPS OVHcloud, et inversement."
updated: 2025-08-26
---

## Objectif

Ce guide vous explique comment transférer une configuration n8n existante vers un VPS OVHcloud, ou depuis un VPS OVHcloud vers une autre instance.
Vous pouvez choisir entre deux méthodes :

* Export/import via les **commandes CLI de n8n**.
* Sauvegarde/restauration du dossier **`.n8n`**.

## Prérequis

* Deux VPS fonctionnels (OVHcloud ou autres).
* Accès SSH administrateur aux deux serveurs.
* Accès à l’interface n8n si vous souhaitez effectuer des exports manuels.

## Méthode 1 : Exporter et importer via la CLI n8n

n8n fournit des commandes pour exporter et importer vos **workflows** et **credentials**.

### Étape 1 - Connectez-vous au VPS source

Ouvrez un terminal et connectez-vous en SSH à votre VPS où n8n est installé :

```bash
ssh <user>@<IP_VPS_SOURCE>
```

### Étape 2 - Exportez les workflows

Exécutez la commande suivante sur votre VPS source pour exporter tous les workflows dans un fichier :

```bash
n8n export:workflow --all --output=workflows.json
```

Pour exporter un workflow spécifique par ID :

```bash
n8n export:workflow --id=<ID> --output=workflow.json
```

### Étape 3 - Exportez les credentials

Exécutez la commande suivante pour exporter tous les credentials dans un fichier :

```bash
n8n export:credentials --all --output=credentials.json
```

> \[!warning]
>
> Si vous migrez vers une autre instance, ajoutez l’option `--decrypted` pour exporter les credentials en clair :
>
> ```bash
> n8n export:credentials --all --decrypted --output=credentials.json
> ```
>
> ⚠️ Manipulez ce fichier avec précaution car il contient des données sensibles.

### Étape 4 - Transférez les fichiers exportés

Copiez les fichiers générés (`workflows.json` et `credentials.json`) vers votre VPS cible :

```bash
scp workflows.json credentials.json <user>@<IP_VPS_CIBLE>:/root/
```

### Étape 5 - Importez les workflows

Connectez-vous en SSH à votre VPS cible :

```bash
ssh <user>@<IP_VPS_CIBLE>
```

Exécutez la commande suivante pour importer les workflows :

```bash
n8n import:workflow --input=workflows.json
```

Pour importer plusieurs workflows depuis un dossier :

```bash
n8n import:workflow --separate --input=backups/
```

### Étape 6 - Importez les credentials

Importez vos credentials avec la commande suivante :

```bash
n8n import:credentials --input=credentials.json
```

Pour importer plusieurs fichiers depuis un dossier :

```bash
n8n import:credentials --separate --input=backups/
```

> \[!primary]
>
> Lors de l’import, si un ID de workflow ou credential existe déjà dans l’instance cible, il sera écrasé.
> Pour éviter les conflits, modifiez ou supprimez l’ID dans les fichiers JSON avant import.

## Méthode 2 : Sauvegarde et restauration du dossier `.n8n`

Cette méthode permet de transférer l’intégralité de la configuration (workflows, credentials et paramètres) entre deux instances.

### Étape 1 - Arrêtez n8n sur le VPS source

Connectez-vous à votre VPS source et exécutez :

```bash
docker stop n8n
```

### Étape 2 - Sauvegardez le dossier `.n8n`

Créez une archive du dossier `.n8n` :

```bash
tar czvf n8n-backup.tar.gz /home/node/.n8n
```

### Étape 3 - Transférez l’archive vers le VPS cible

Envoyez le fichier vers votre VPS cible :

```bash
scp n8n-backup.tar.gz <user>@<IP_VPS_CIBLE>:/root/
```

### Étape 4 - Restaurez l’archive sur le VPS cible

Connectez-vous au VPS cible et exécutez :

```bash
tar xzvf n8n-backup.tar.gz -C /home/node/.n8n
```

### Étape 5 - Redémarrez n8n

Toujours sur le VPS cible, relancez n8n :

```bash
docker start n8n
```

> \[!warning]
>
> Cette méthode nécessite que la **clé de chiffrement (`encryptionKey`)** soit identique entre les deux instances.
> Vérifiez ou copiez ce paramètre depuis le fichier de configuration de votre instance source.

## DNS et SSL

Après la migration, si le domaine ou le sous-domaine change (par exemple `n8n.mydomain.com` → `n8n.ovh.net`), mettez à jour :

* La variable `N8N_HOST` dans votre fichier `docker-compose.yml`.
* Votre zone DNS pour que le sous-domaine pointe vers l’adresse IP du nouveau VPS.

Pour en savoir plus, consultez notre guide :
[Modifier une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)

## Conclusion

Vous disposez désormais de deux méthodes pour migrer vos workflows et credentials n8n vers un VPS OVHcloud (ou depuis OVHcloud vers un autre environnement) :

* **Export/Import via CLI** : simple et sélectif.
* **Sauvegarde `.n8n`** : complet, idéal pour une migration totale.

Pour plus d’informations, référez-vous à la [documentation officielle n8n](https://docs.n8n.io/hosting/cli-commands/).

## Aller plus loin