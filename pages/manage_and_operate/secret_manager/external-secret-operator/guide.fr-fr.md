---
title: "Utiliser Kubernetes External Secret Operator avec Secret Manager"
excerpt: "Configurer External Secret Operator pour stocker des secrets Kubernetes sur le Secret Manager OVHcloud"
updated: 2025-10-27
---

> [!primary]
> Le Secret Manager est actuellement en phase bêta. Ce guide est susceptible d’être mis à jour ultérieurement avec les avancées de nos équipes en charge de ce produit.
>

## Objectif

Ce guide explique comment configurer le Kubernetes External Secret Operator pour utiliser le Secret Manager OVHcloud comme fournisseur

## Prérequis

- Un [compte client OVHcloud](/pages/account_and_service_management/account_information/ovhcloud-account-creation).
- Avoir [commandé un domaine OKMS](/pages/manage_and_operate/kms/quick-start) ou [créé un premier secret](/pages/manage_and_operate/secret_manager/secret-manager-ui).

## En pratique

### Configuration du Secret Manager

Pour permettre l'accès au Secret Manager, vous devrez créer des identifiants.

Créez un [utilisateur local IAM](/pages/account_and_service_management/account_information/ovhcloud-users-management) avec les droits d'accès à votre domaine.
Cet utilisateur doit avoir au moins les droits suivants :

- `okms:apikms:secret/create`
- `okms:apikms:secret/version/getData`
- `okms:apiovh:secret/get`
- `okms:apikms:secret/create`

Puis créez un jeton d'accès personnel (PAT) `user_pat` :

> [!api]
>
> @api {v1} /me POST /me/identity/user/{user}/token

Vous aurez également besoin de l'`okms-id` du domaine OKMS que vous souhaitez utiliser. Cet ID peut être trouvé sur l'espace client OVHcloud.

### Configuration de Sealed Secret

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

#### Utilisation

- Créez votre Sealed Secret

```bash
kubeseal -f <secret-file> \
        -w <sealedsecret-output-file> \
        --controller-name=sealed-secrets \
        --controller-namespace=kube-system

kubectl create  -f <sealedsecret-output-file>

# Vérifiez si vous avez accès à votre Secret d'origine
kubectl get secrets <your-secret-name> -o yaml
```

Vous pouvez maintenant supprimer `secret-file` et utiliser `sealedsecret-output-file` à la place pour un stockage plus sécurisé

- Supprimez votre Sealed Secret

```bash
kubectl delete sealedsecret <your-sealedsecret-name>
```

#### Exemple

```bash
$ cat secret.yaml 
apiVersion: v1
kind: Secret
metadata:
  name: secret
type: Opaque
data:
  value: TVkgQkFTRTY0IEVOQ09ERUQgU0VDUkVUIFZBTFVF

$ kubeseal -f secret.yaml \
           -w sealed-secret.yaml \
           --controller-name=sealed-secrets \
           --controller-namespace=kube-system

$ cat sealed-secret.yaml 
---
apiVersion: bitnami.com/v1alpha1
kind: SealedSecret
metadata:
  name: secret
  namespace: default
spec:
  encryptedData:
    value: AgBLSGW9eG8Lc0HbToTM884euTNp49M6AkauFadPI8GwKe/lfSEmLr16HEQnh7DPb7T8OgL3d7qMRucEWO2TSppxsoXS5whKDaX7XA+d5tLSPZR6TCgI+ZWYBCYcerp8fM3gkzixM4wlyxAevqsWPxazGNQM4eYBv0YFZ+kaffkougHjG5uLwuX1IWGE8pFMf5XszkXu3MoFtmf2lbop+2qEtS3Wr4k/ueL92dY3ZmP1ZHSXWgvnNfZ30H1t+4pn9K+ddlJrajC/8TVT811WylyISd7EG6HaO8ayNRDErsu/JjsworJBKdj1vMIsdE+0ZQFg1MmCKp0zWU0Xjp90cEhSXuq9eqp4A8pofZ6D5n7ERr4jmznb41WWHRcKj2BdZBsOBUlP/J7P2Ymseet8+8od1HX0XQOv1CEnLHF6GMNAFZ7aQckuUIwKMx+zEHT6qVNBbtNe2B1OP1ApwRUw6lEdP5AnToi/mNt3ilypuTwXMqVGbHJzNMUrQRhfDItPALpDknCIcu1j1QsQRFIrdQ0Gfheg+QIzYJKVErWCRGR9zEUkqsMcxM7ruEc5U1GAgYyfLvXkczxzUG2WXf5mszKWyfcnQfCwmNdF/WKsufeJI0FaVQaWpkgX2cvTSd0281rKLvwEv0NRBVJkZ0lL1mzoZMXzXP5uWyk0E9SCHwM261ZkvqLsxnpKVA2QDZ4SuMBvl2fdIle5WVO/U1sl1eRAK1BVEWg8pYE7mTE7cXE=
  template:
    metadata:
      name: secret
      namespace: default
    type: Opaque

$ kubectl create -f sealed-secret.yaml 
sealedsecret.bitnami.com/secret created

$ kubectl get secrets secret -o yaml                   
apiVersion: v1
data:
  value: TVkgQkFTRTY0IEVOQ09ERUQgU0VDUkVUIFZBTFVF
kind: Secret
metadata:
  creationTimestamp: "2025-10-13T12:37:25Z"
  name: secret
  namespace: default
  ownerReferences:
  - apiVersion: bitnami.com/v1alpha1
    controller: true
    kind: SealedSecret
    name: secret
    uid: c3a8489f-8125-406b-8a3a-f99b82d432e1
  resourceVersion: "16156798047"
  uid: f3fbfd60-46d7-4211-a9b1-e67d452bc7dc
type: Opaque
```

Plus d'informations : (<https://github.com/bitnami-labs/sealed-secrets>)

### Configuration du Secret Provider dans Kubernetes

#### Installez l'External Secret Operator sur votre Kubernetes

```bash
helm repo add external-secrets https://charts.external-secrets.io

helm install external-secrets \
external-secrets/external-secrets \
-n external-secrets \
--create-namespace \
--set installCRDs=true
```

#### Configurer l'External Secret Operator

Tout d'abord, configurez un `SecretStore` qui est chargé de la synchronisation avec le Secret Manager.
Nous configurons le SecretStore en utilisant HashiCorp Vault avec l'authentification par jeton et en utilisant l'endpoint OKMS comme backend.

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

La ressource `SecretStore` :

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

#### Utiliser External Secret Operator

Une fois le `SecretStore` configuré, vous pouvez définir des `ExternalSecret` provenant du gestionnaire de secrets.
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
