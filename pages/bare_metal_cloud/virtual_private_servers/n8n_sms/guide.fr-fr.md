---

title: "Automatiser l'envoie de SMS avec n8n via l'API OVHcloud"
excerpt: "Découvrez comment envoyer des SMS depuis n8n en utilisant l'API OVHcloud."
updated: 2025-07-15
---

## Objectif

Ce guide vous explique comment intégrer l'API SMS d'OVHcloud dans **n8n**, afin d'envoyer automatiquement des SMS depuis vos workflows. Vous apprendrez à configurer un appel HTTP signé via l'API OVH pour déclencher l'envoi d’un message.


## Prérequis

- Disposer d'un compte OVHcloud actif avec le service **SMS** activé
- Des **crédentiels API OVHcloud** (application key, application secret, consumer key)
- Un numéro d’expéditeur (ex : votre nom ou numéro valide déclaré dans le Manager OVHcloud)
- Un VPS, un serveur ou un poste local avec [n8n](https://n8n.io/) installé et accessible

## En pratique

### Étape 1 – Générer les identifiants API OVHcloud

Avant de pouvoir envoyer des SMS via l’API OVHcloud, vous devez récupérer les trois identifiants suivants :

- Application key
- Application secret
- Consumer key

Consultez la section « Utilisation avancée : coupler les API OVHcloud avec une application » de notre guide [Premiers pas avec les API OVHcloud](/pages/manage_and_operate/api/first-steps) puis copiez et conservez les trois identifiants `Application key`, `Application secret` et `Consumer key`.

## Étape 2 – Générer une signature API OVHcloud depuis un service externe

L’API OVHcloud exige une signature HMAC-SHA1 qui n’est pas générable directement dans un nœud `Code` N8N, car la bibliothèque `crypto` de Node.js n’est pas disponible dans cet environnement.

### Solution recommandée : créer un mini service Node.js sur votre VPS

Cette solution consiste à créer un petit script Node.js qui sera exposé via une API locale. Il générera pour vous la signature attendue par OVHcloud.

### 1. Créer le script sur votre VPS

1. Connectez-vous à votre VPS.
2. Déplacez-vous dans un dossier adapté, par exemple :

   ```bash
   cd /opt
   mkdir n8n-signature-api && cd n8n-signature-api
   ```
3. Créez un fichier `index.js` :

   ```bash
   nano index.js
   ```
4. Collez ce code dans le fichier :

```js
const express = require('express');
const crypto = require('crypto');
const cors = require('cors');
const app = express();
app.use(cors());
app.use(express.json());

const applicationSecret = 'VOTRE_APPLICATION_SECRET';

app.post('/sign', (req, res) => {
  const { consumerKey, method, url, body, timestamp } = req.body;
  const toSign = `${applicationSecret}+${consumerKey}+${method}+${url}+${body}+${timestamp}`;
  const signature = '$1$' + crypto.createHmac('sha1', applicationSecret).update(toSign).digest('hex');
  res.json({ signature });
});

app.listen(3000, () => console.log('Signer API prêt sur http://localhost:3000'));
```

Remplacez `VOTRE_APPLICATION_SECRET` par votre application secret.

5. Installez les dépendances :

```bash
npm init -y
npm install express cors
```

6. Lancez le serveur :

```bash
node index.js
```

Le service est maintenant accessible sur `http://[IP_DE_VOTRE_VPS]:3000/sign`.

Si vous utilisez Docker ou souhaitez exposer cette API, pensez à ouvrir le port 3000 ou utiliser un proxy (comme Caddy ou NGINX).

### Étape 3 – Créer le workflow dans N8N

#### 1. Créer un nœud `Set` pour stocker les variables globales

1. Connectez-vous à votre interface n8N
2. Cliquez sur le bouton **Create Workflow**.
3. Ajoutez un nœud de type **Set** et nommez-le par exemple `Set - Credentials`. Pour plus de détails concernant la création de nœud, consultez la [documentation officielle de n8n](https://docs.n8n.io/integrations/creating-nodes/overview/).

Ajoutez un nœud de type `Set` avec les valeurs suivantes :

- Name : applicationKey / Value : "VOTRE_APPLICATION_KEY"
- Name : consumerKey / Value : "VOTRE_CONSUMER_KEY"
- Name : serviceName / Value : "sms-ovh-123456"

Transformer en tableau

Ces champs seront utilisés dynamiquement dans les nœuds suivants.

#### 2. Créer un nœud `HTTP Request` vers le service `/sign`

Ajoutez un nœud `HTTP Request` et nommez-le `Sign - Generate Signature`. Appliquez la configuration suivante :

* **HTTP Method** : `POST`
* **URL** : `http://[IP_DE_VOTRE_VPS]:3000/sign`
* **Request Format** : `JSON`
* Cliquez sur **Add Parameter** → `Body Parameters` → Ajoutez les paramètres suivants :

| Name          | Value       |
| ------------- | ----------------------------------------------- |
| `method`      | `POST`                                          |
| `url`         | `https://eu.api.ovh.com/1.0/sms/{{ $node["Set - Credentials"].json["serviceName"] }}/jobs`      |
| `body`        | `{"charset":"UTF-8","coding":"7bit","message":"Message test","noStopClause":true,"priority":"high","receivers":["33600000000"],"sender":"MonEntreprise"}` |
| `timestamp`   | `{{ Math.floor(Date.now() / 1000) }}`                 |
| `consumerKey` | `{{ $node["Set - Credentials"].json["consumerKey"] }}`    |

Cela appellera le service VPS pour générer la signature.

#### 3. Créer un nœud `HTTP Request` vers OVH pour envoyer le SMS

Ajoutez un troisième nœud `HTTP Request`, et nommez-le `SMS - Send`.

* **HTTP Method** : `POST`
* **URL** : `https://eu.api.ovh.com/1.0/sms/{{ $node["Set - Credentials"].json["serviceName"] }}/jobs`
* **Headers** : cliquez sur **Add Header** et remplissez :

| Name              | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| Content-Type      | `application/json`                                           |
| X-Ovh-Application | `{{ $node["Set - Credentials"].json["applicationKey"] }}`    |
| X-Ovh-Timestamp   | `{{ $node["Sign - Generate Signature"].json["timestamp"] }}` |
| X-Ovh-Signature   | `{{ $node["Sign - Generate Signature"].json["signature"] }}` |
| X-Ovh-Consumer    | `{{ $node["Set - Credentials"].json["consumerKey"] }}`       |

* **Body Content Type** : `Raw`
* **Content Type** : `application/json`
* **Body** : collez ce contenu directement dans le champ :

```json
{
  "charset": "UTF-8",
  "coding": "7bit",
  "message": "Message test",
  "noStopClause": true,
  "priority": "high",
  "receivers": ["33600000000"],
  "sender": "MonEntreprise"
}
```

**Important** : ne mettez pas de variable ici, ne l'entourez pas d'expressions `{{ }}`, ni de `stringify` — c'est du JSON brut.

#### 4. Relier les nœuds entre eux dans N8N

Dans l'interface de N8N, reliez les nœuds dans cet ordre :

```
Start → Set - Credentials → Sign - Generate Signature → SMS - Send
```

Pour relier deux nœuds, cliquez sur le petit carré gris à droite du premier nœud, puis faites glisser jusqu'au carré gauche du nœud suivant.

### Tester votre workflow

Exécutez votre workflow. Les étapes suivantes s'éxécutent :

1. Récupère les identifiants via `Set`
2. Génère dynamiquement la signature via le service `/sign`
3. Appelle l’API OVH pour envoyer le SMS

Le message est alors transmis via l’API OVHcloud à votre destinataire.

#### Erreurs fréquentes

##### Problem in node : The service refused the connection - perhaps it is offline

Cela signifie que N8N ne peut pas contacter votre serveur de signature. Voici les points à vérifier :

1. Le serveur Node.js est-il lancé ?

Exécutez dans votre terminal :

node index.js

Vous devez voir :

Signer API prêt sur http://localhost:3000

2. Utilisez-vous la bonne IP dans l’URL ?

Ne mettez pas localhost dans N8N sauf si N8N et votre script sont sur la même machine.

Utilisez l’adresse IP publique de votre VPS : http://[IP_DE_VOTRE_VPS]:3000/sign

3. Le port 3000 est-il ouvert ?

Sur un serveur Ubuntu avec UFW :

sudo ufw allow 3000/tcp

Vérifiez également les règles de pare-feu côté OVH / hébergeur.

4. L’URL est-elle correcte dans le nœud HTTP vers /sign ?

Elle doit pointer vers : http://[IP_DE_VOTRE_VPS]:3000/sign

Corrigez ces éléments et relancez le workflow.

##### Bad request – please check your parameters

Cela signifie que la requête envoyée à l’API OVH est mal formée. Voici les causes fréquentes :

Le JSON dans le Body est-il bien formé ?

Utilisez bien le type Raw, Content-Type: application/json et collez un JSON propre (pas d'expressions {{ }} ni de stringify).

Le numéro dans receivers est-il bien au format international ?

Exemple correct : "33612345678" (sans espace, sans +)

Le champ sender est-il déclaré dans votre espace OVH ?

Il doit être validé côté OVH sinon la requête échouera.

Les headers contiennent-ils tous les bons champs ?

X-Ovh-Application, X-Ovh-Timestamp, X-Ovh-Signature, X-Ovh-Consumer, Content-Type

La signature générée est-elle correcte ?

Vérifiez que le corps utilisé pour signer (body) est identique à celui envoyé.

Astuce : si le problème persiste, remplacez temporairement le corps par un exemple minimal et remontez les paramètres un par un.

