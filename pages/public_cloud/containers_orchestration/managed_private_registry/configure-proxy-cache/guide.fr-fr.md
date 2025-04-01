---
title: Configure Proxy Cache on an OVHcloud Managed Private Registry
excerpt: 'Find out how to configure Proxy Cache on an OVHcloud Managed Private Registry'
updated: 2025-04-01
---

# User Guide: Using Proxy Cache for Docker Hub in Managed Private Registry

## Overview  
Harbor provides a **proxy cache** feature that helps you mirror and cache images from external registries like **Docker Hub**. This improves performance and reduces rate limits imposed by external registries.  

We **strongly recommend** using a **Docker account** (even a free one) to **avoid rate limits** when pulling images. Without authentication, Docker Hub enforces strict pull limits, which may cause failures when pulling frequently used images.  

> **Note**: Harbor **only supports proxy caching for Docker Hub and other Harbor registries**. Other container registries are **not supported** for proxy caching.  

---

## Prerequisites  
- A running **Managed Private Registry**.  
- Access to **Harbor Web UI** (with admin access).  
- A **Docker Hub account** (recommended to prevent rate limits).  

---

## Step-by-Step Guide  

### 1. Enable Proxy Cache

1. Log in to [**Harbor Web UI**](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-connect-to-ui?id=kb_article_view&sysparm_article=KB0055926) as an **Administrator**.  
2. Go to **Administration** → **Registries**.  
3. Click **+ New Endpoint**, then select **Docker Hub** as the provider.  
4. Fill in the details:  
   - **Registry Type**: Docker Hub  
   - **Registry Name**: (e.g., `docker-hub-proxy`)  
   - **Registry Endpoint**: `https://hub.docker.com`  
   - **Access ID**: *(your Docker Hub username)*  
   - **Access Secret**: *(your Docker Hub password or personal access token)*  
5. Click **OK**.  

> **Note**: If you do not provide Docker Hub credentials, your requests may hit **rate limits** (10 pulls/hour per IPV4 for anonymous users).  

<img src="images/registry-proxy-cache-001.png"  width="500"/>
---

### 2. Create a Proxy Cache Project

1. In **Harbor Web UI**, go to **Projects**.  
2. Click **+ New Project**.  
3. Enter a **Project Name** (e.g., `docker-hub-mirror`).  
4. Select **Proxy Cache**.  
5. Under **Upstream Registry**, choose the **Docker Hub proxy registry** created earlier.  
6. Click **Save**.  

> **Note**: By default, Harbor creates a **7 day retention policy** for each new proxy cache project. See more about [Tag Retention Policies](https://goharbor.io/docs/2.1.0/working-with-projects/working-with-images/create-tag-retention-rules/).  

<img src="images/registry-proxy-cache-002.png"  width="500"/>

---

### 3. Configure Docker to Use Harbor Proxy Cache  

#### Login to Managed Private Registry 
```sh
docker login <your-managed-registry-domain> -u <username> -p <password>
```

#### Pull Images via Proxy Cache
Instead of pulling directly from Docker Hub, use your **Private Managed Registry** as an intermediary:

```bash
docker pull <your-managed-registry-domain>/dockerhub-mirror/library/nginx:latest
```

Harbor will cache the image locally, so subsequent pulls will be much faster and won’t count against Docker Hub rate limits.
## Supported Proxy Cache Registries

Harbor only supports proxy caching for:
- ✅ Docker Hub
- ✅ Harbor registries (another Harbor instance)

Other container registries (e.g., Amazon ECR, Google Container Registry, Quay.io, etc.) are not supported for proxy caching.

## Benefits of Using Proxy Cache

- ✅ Avoid Docker Hub rate limits (with authentication).
- ✅ Faster image pulls for frequently used images.
- ✅ Reduced dependency on external registries.
- ✅ Improved reliability by caching images locally.

## Troubleshooting

### 1. Getting "Too Many Requests" Errors

- Ensure you configured Docker Hub authentication in Harbor.
- Log in to Harbor before pulling images:
  ```bash
  docker login <your-managed-registry-domain>
  ```

### 2. Image Not Found in Proxy Cache

- If the image has not been pulled before, Harbor will fetch it from Docker Hub. Try again in a few moments.
- Check the proxy cache project settings in Harbor to ensure it's linked to the correct registry.



## Conclusion

Using Harbor's proxy cache helps optimize Docker image pulls, avoiding rate limits and improving performance. However, only Docker Hub and Harbor registries are supported for proxy caching. Be sure to authenticate with Docker Hub in Harbor to prevent rate limit issues.

