---
title: "Use Kubernetes External Secret Operator with Secret Manager"
excerpt: "Configure External Secret Operator to store Kubernetes secrets on the OVHcloud Secret Manager"
updated: 2025-11-07
---

> [!primary]
> Secret Manager is currently in beta phase. This guide can be updated in the future with the advances of our teams in charge of this product.

## Objective

This guide explains how to set up the Kubernetes External Secret Operator to use the OVHcloud Secret Manager as a provider.

## Requirements

- An [OVHcloud customer account](/pages/account_and_service_management/account_information/ovhcloud-account-creation).
- Have [ordered an OKMS domain](/pages/manage_and_operate/kms/quick-start) or [created a first secret](/pages/manage_and_operate/secret_manager/secret-manager-ui).
- Have a Kubernetes cluster.

## Instructions

### Setup the Secret Manager

To allow access to the Secret Manager you will need to create credentials.

Create an [IAM local user](/pages/account_and_service_management/account_information/ovhcloud-users-management) with access right on your domain.

The user should be a member of a group with the ADMIN role, or if using [IAM policies](/pages/account_and_service_management/account_information/iam-policy-ui) to have at least the following rights on the OKMS domain:

- `okms:apikms:secret/create`
- `okms:apikms:secret/version/getData`
- `okms:apiovh:secret/get`

Then create a Personnal Acces Token (PAT) `user_pat`:

> [!api]
>
> @api {v1} /me POST /me/identity/user/{user}/token

API will answer with:

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

Keep safe the value of `token` field as it will never be prompt again and will be used to authenticate on the Secret Manager as `user_pat`.

You will also need the `okms-id` of the OKMS domain you want to use. This ID can be found on the OVHcloud Control Panel.

### Setup Sealed Secret (optionnal)

Sealed Secret allows you to safely store Kubernetes Secrets wherever you want by encrypting them.
This step is optionnal but highly recommended.

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

More information: (<https://github.com/bitnami-labs/sealed-secrets>)

### Setup the Secret Provider in Kubernetes

#### Install the External Secret Operator on your kubernetes

```bash
helm repo add external-secrets https://charts.external-secrets.io
helm repo update

helm install external-secrets \
external-secrets/external-secrets \
-n external-secrets \
--create-namespace \
```

#### Configure External Secret Operator

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

The `SecretStore` resource:

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

Region name can be translated from your region location using:

> [!api]
>
> @api {v1} /location GET /location

As an example for **Europe (France - Paris)**, OKMS endpoint is **eu-west-par.okms.ovh.net**

#### Use External Secret Operator

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

> [!info]
> Only `ExternalSecret` are supported yet.

#### Deploy your application

The secret should be created and available in kubernetes.

For any additionnal informations on how to manage the External Secret Operator refer to the dedicated documentation, using the HashiCorp Vault provider: <https://external-secrets.io/latest/>.

## Go further

Join our [community of users](/links/community).
