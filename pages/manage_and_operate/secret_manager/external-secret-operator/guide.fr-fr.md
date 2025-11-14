---
title: "Utiliser Kubernetes External Secret Operator avec Secret Manager"
excerpt: "Configurer External Secret Operator pour stocker des secrets Kubernetes sur le Secret Manager OVHcloud"
updated: 2025-11-07
---

> [!primary]
> Le Secret Manager est actuellement en phase bêta. Ce guide est susceptible d’être mis à jour ultérieurement avec les avancées de nos équipes en charge de ce produit.
>

## Objectif

Ce guide explique comment configurer le Kubernetes External Secret Operator pour utiliser le Secret Manager OVHcloud comme fournisseur

## Prérequis

- Un [compte client OVHcloud](/pages/account_and_service_management/account_information/ovhcloud-account-creation).
- Avoir [commandé un domaine OKMS](/pages/manage_and_operate/kms/quick-start) ou [créé un premier secret](/pages/manage_and_operate/secret_manager/secret-manager-ui).
- Avoir un cluster Kubernetes.

## En pratique

### Configuration du Secret Manager

Pour permettre l'accès au Secret Manager, vous devrez créer des identifiants.

Créez un [utilisateur local IAM](/pages/account_and_service_management/account_information/ovhcloud-users-management) avec les droits d'accès à votre domaine.

Cet utilisateur doit être membre d'un groupe avec le role ADMIN, ou si vous utilisez les [politiques IAM](/pages/account_and_service_management/account_information/iam-policy-ui) avoir au moins les droits suivants sur le domaine OKMS :

- `okms:apikms:secret/create`
- `okms:apikms:secret/version/getData`
- `okms:apiovh:secret/get`

Puis créez un jeton d'accès personnel (PAT) `user_pat` :

> [!api]
>
> @api {v1} /me POST /me/identity/user/{user}/token

L'API va répondre :

```json
{
  "creation": "2025-11-13T10:38:44.658926311Z",
  "description": "my first PAT",
  "expiresAt": null,
  "lastUsed": null,
  "name": "my_PAT",
  "token": "eyJhbGciOiJFZERXXXXXXXXDyI23Q7euIDmw9Pn__SDA"
}
```

Gardez en sécurité la valeur du champ `token` car il ne sera jamais réaffiché et sera utilisé pour l'authentification sur le Secret Manager comme `user_pat`.

Vous aurez également besoin de l'`okms-id` du domaine OKMS que vous souhaitez utiliser. Cet ID peut être trouvé sur l'espace client OVHcloud.

### Configuration de Sealed Secret (optionnel)

Sealed Secret vous permet de stocker en toute sécurité des Secrets Kubernetes là où vous le souhaitez en les chiffrant.
Cette étape est optionnelle mais fortement recommandée.

Tout d'abord, installez le contrôleur dans votre cluster. Il déchiffrera automatiquement les Sealed Secrets en Secrets Kubernetes standards

```bash
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets
helm install sealed-secrets -n kube-system sealed-secrets/sealed-secrets
```

Puis, installez la cli kubeseal pour chiffrer des Secrets en Sealed Secrets

```bash
KUBESEAL_VERSION='' # Définissez ceci sur, par exemple, KUBESEAL_VERSION='0.23.0'
curl -OL "https://github.com/bitnami-labs/sealed-secrets/releases/download/v${KUBESEAL_VERSION:?}/kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz"
tar -xvzf kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz kubeseal
sudo install -m 755 kubeseal /usr/local/bin/kubeseal
```

Plus d'informations : (<https://github.com/bitnami-labs/sealed-secrets>)

### Configuration du Secret Provider dans Kubernetes

#### Installez l'External Secret Operator sur votre Kubernetes

```bash
helm repo add external-secrets https://charts.external-secrets.io
helm repo update

helm install external-secrets \
external-secrets/external-secrets \
-n external-secrets \
--create-namespace \
```

#### Configurer l'External Secret Operator

Tout d'abord, configurez un `ClusterSecretStore` qui est chargé de la synchronisation avec le Secret Manager.
Nous configurons le ClusterSecretStore en utilisant HashiCorp Vault avec l'authentification par jeton et en utilisant l'endpoint OKMS comme backend.

Ajoutez le `user_pat` en tant que secret pour pouvoir l'utiliser dans les chartes.

```yaml
---
apiVersion: bitnami.com/v1alpha1
kind: SealedSecret
metadata:
  name: token-secret
  namespace: default
spec:
  encryptedData:
      token: <user_pat>
  template:
      metadata:
        name: token-secret
        namespace: default
        type: Opaque
```

La ressource `ClusterSecretStore` :

```yaml
apiVersion: external-secrets.io/v1
kind: ClusterSecretStore
metadata:
  name: vault-secret-store
spec:
  provider:
      vault:
        server: "https://{region}.okms.ovh.net/api/<okms_id>" # endpoint OKMS, complétez avec la région correcte et votre okms_id 
        path: "secret"
        version: "v2" 
        auth:
            tokenSecretRef:
              name: token-secret # Le secret k8s contenant votre PAT
              key: token 
```

> [!info]
> Seulement [l'authentification par token](https://external-secrets.io/latest/provider/hashicorp-vault/#token-based-authentication) est supporté

Le nom de la région peut être traduit de la localisation avec:

> [!api]
>
> @api {v1} /location GET /location

Par exemple pour **Europe (France - Paris)**, l'endpoint OKMS est **eu-west-par.okms.ovh.net**

#### Utiliser External Secret Operator

Une fois le `ClusterSecretStore` configuré, vous pouvez définir des `ExternalSecret` provenant du gestionnaire de secrets.
Dans l'exemple, nous utilisons un secret déjà créé sur le Secret Manager :

- Path : `prod/database/MySQL`
- Value :
  - `login: admin`
  - `password: my_secret_password`

```yaml
apiVersion: external-secrets.io/v1
kind: ExternalSecret
metadata:
  name: vault-external-secret
  namespace: default
spec:
  secretStoreRef:
    name: vault-secret-store
    kind: ClusterSecretStore
  refreshInterval: "10s"
  target:
    name: creds-secret
    creationPolicy: Owner
  data:
    - secretKey: login
      remoteRef:
        key: prod/database/MySQL # Chemin du secret dans le Secret Manager
        property: login # Clé à trouver dans les données JSON du secret
    - secretKey: password
      remoteRef:
        key: prod/database/MySQL
        property: password
```

> [!info]
> Uniquement les `ExternalSecret` sont supporté pour l'instant.

#### Déployez votre application

Le secret devrait être créé et disponible dans Kubernetes.

Pour toute information supplémentaire sur la gestion de l'External Secret Operator, reportez-vous à la documentation dédiée, en utilisant le fournisseur HashiCorp Vault : <https://external-secrets.io/latest/>.

## Aller plus loin

Rejoignez notre [communauté d'utilisateurs](/links/community).
