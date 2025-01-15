---
title: Pricing and Management of OVHcloud NSX Edges
excerpt: A guide on pricing options, configurations, and customization of NSX Edges for VMware on OVHcloud.
updated: 2025-01-15
---
# Information on Pricing and Configurations of NSX Edges

## Objective
This documentation aims to explain the configuration options for NSX Edges and the steps to manage them within a VMware environment on OVHcloud. It also outlines technical limitations and provides guidance on how to adapt these configurations to specific needs.

---

## Prerequisites
- **Access to the OVHcloud Manager interface** to manage your NSX Edges.
- **Use of VMware NSX 4.1.1** to access customization options.
- A basic understanding of VMware concepts and NSX Edge features.

---

## General Overview
### Default Configuration
When creating a VMware environment, OVHcloud automatically provides:
- **2 Medium NSX Edges**:
  - 4 vCPU.
  - 8 GB RAM.

This default configuration meets most standard requirements for connectivity and network security.

### Customization
You can adapt your infrastructure to meet your specific needs:

1. **NSX Edge Sizes**:
   - Medium: 4 vCPU, 8 GB RAM.
   - Large: 8 vCPU, 32 GB RAM.
   - XL: 16 vCPU, 64 GB RAM.

2. **Number of NSX Edges**:
   - Minimum: 2 (default configuration).
   - Maximum: Up to **10 NSX Edges per cluster**.

### Limitations
- **1 NSX Edge cluster per vDC**.
- **10 NSX Edges maximum per cluster** (Broadcom/VMware limitation).
- NSX version 4.0.1 does not support:
  - Ordering new vDCs under NSX 4.1.1.
  - Modifying or adding NSX Edges.

---

## Practical Guide
### Steps to Customize NSX Edges
1. **Order new NSX Edges**:
   - Log in to the OVHcloud Manager interface.
   - Navigate to the **Network** section of the Datacenter dashboard, then access **NSX Edges**.
   - Click on "Add an Edge" and select the desired size.
   > All Edges must be the same size: when adding a new Edge, it will automatically match the size of existing Edges.

2. **Modify the size of existing NSX Edges**:
   - Access the list of NSX Edges in the Manager.
   - Select the Edge you want to modify.
   - Choose a new size (Medium, Large, or XL) and apply the changes.

3. **Remove unused NSX Edges**:
   - Identify the Edge to be removed in the Manager interface.
   - Click on "Delete" and confirm the action.
   
   **Note**: The Edge must be in resilience mode before deletion to ensure no ongoing traffic is affected.

---

## Learn More
- For detailed information on NSX Edge features, consult the [VMware NSX technical documentation](https://www.vmware.com/products/nsx.html).
- Pricing details for NSX Edges are not included in this documentation. To access up-to-date pricing or request a quote, visit the OVHcloud website or contact support through your client area.
