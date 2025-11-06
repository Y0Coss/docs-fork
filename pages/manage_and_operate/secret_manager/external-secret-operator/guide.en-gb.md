---
title: "Use Kubernetes External Secret Operator with Secret Manager"
excerpt: "Configure External Secret Operator to store Kubernetes secrets on the OVHcloud Secret Manager"
updated: 2025-10-27
---

> [!primary]
> Secret Manager is currently in beta phase. This guide can be updated in the future with the advances of our teams in charge of this product.

## Objective

This guide explains how set up the Kubernetes External Secret Operator to use the OVHcloud Secret Manager as a provider

## Requirements

- An [OVHcloud customer account](/pages/account_and_service_management/account_information/ovhcloud-account-creation).
- Have [ordered an OKMS domain](/pages/manage_and_operate/kms/quick-start) or [created a first secret](/pages/manage_and_operate/secret_manager/secret-manager-ui).

## Instructions

### Setup the Secret Manager

To allow access to the Secret Manager you will need to create credentials.

Create an [IAM local user](/pages/account_and_service_management/account_information/ovhcloud-users-management) with acces right on your domain.
This user need to have at least the following rights:

- `okms:apikms:secret/create`
- `okms:apikms:secret/version/getData`

Then create a Personnal Acces Token (PAT) `user_pat`:

> [!api]
>
> @api {v1} /me POST /me/identity/user/{user}/token

You will also need the `okms-id` of the OKMS domain you want to use. This ID can be found on the OVHcloud Control Panel.

### Setup Sealed Secret

Sealed Secret allows you to safely store Kubernetes Secrets wherever you want by encrypting them.
This step is optionnal but highly recommendated.

First, install the controller in your cluster.  It will automatically decrypt Sealed Secrets into standard Kubernetes Secrets

```bash
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets
helm install sealed-secrets -n kube-system sealed-secrets/sealed-secrets
```

Then, install kubeseal cli to encrypt Secrets into Sealed Secrets

```bash
KUBESEAL_VERSION='' # Set this to, for example, KUBESEAL_VERSION='0.23.0'
curl -OL "https://github.com/bitnami-labs/sealed-secrets/releases/download/v${KUBESEAL_VERSION:?}/kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz"
tar -xvzf kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz kubeseal
sudo install -m 755 kubeseal /usr/local/bin/kubeseal
```

#### Usage

- Create your Sealed Secret

```bash
kubeseal -f <secret-file> \
        -w <sealedsecret-output-file> \
        --controller-name=sealed-secrets \
        --controller-namespace=kube-system

kubectl create  -f <sealedsecret-output-file>

# Check if you have access to your original Secret
kubectl get secrets <your-secret-name> -o yaml
```

You can now delete `secret-file` and use `sealedsecret-output-file` instead for a more secure storage

- Delete your Sealed Secret

```bash
kubectl delete sealedsecret <your-sealedsecret-name>
```

#### Example

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

More information: (<https://github.com/bitnami-labs/sealed-secrets>)

### Setup the Secret Provider in Kubernetes

#### Install the External Secret Operator on your kubernetes

```bash
helm repo add external-secrets https://charts.external-secrets.io

helm install external-secrets \
external-secrets/external-secrets \
-n external-secrets \
--create-namespace \
--set installCRDs=true
```

#### Define the External Secret Operator charts

First, setup a `SecretStore` that is responsible of the synchronization with the Secret Manager.
We configure the SecretStore using HashiCorp Vault with token authentification and with the OKMS endpoint as backend.

Add the `user_pat` as a secret to be able to use it in the charts.

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

The `SecretStore` chart:

```yaml
apiVersion: external-secrets.io/v1
kind: ClusterSecretStore
metadata:
name: vault-secret-store
spec:
provider:
    vault:
    server: "https://{region}.okms.ovh.net/api/<okms_id>" # OKMS endpoint, fill with the correct region and your okms_id 
    path: "secret"
    version: "v2" 
    auth:
        tokenSecretRef:
        name: token-secret # The k8s secret that contain your PAT
        key: token 
```

> [!info]
> Only [token authentication](https://external-secrets.io/latest/provider/hashicorp-vault/#token-based-authentication) is supported

Once the `SecretStore` is setup you can define `ExternalSecret` that comes from the secret manager.
In the example we use a secret already created on the Secret Manager:

- Path: `prod/database/MySQL`
- Value:
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
        key: prod/database/MySQL # Path of the secret in the Secret Manager
        property: login # Key to find in the JSON data of the secret
    - secretKey: password
    remoteRef:
        key: prod/database/MySQL
        property: password
```

#### Deploy your application

The secret should be created and available in kubernetes.

For any additionnal informations on how to manage the External Secret Operator refer to the dedicated documentation, using the HashiCorp Vault provider: <https://external-secrets.io/latest/>.

## Go further

Join our [community of users](/links/community).
