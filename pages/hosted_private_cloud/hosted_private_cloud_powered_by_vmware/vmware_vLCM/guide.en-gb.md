---
title: Updating hosts using vSphere Lifecycle Management (vLCM)
excerpt: Learn how to update your ESXi hosts via vSphere Lifecycle Management—quickly and securely.
updated: 2025-04-14
---

## Objective

This guide explains how to update your ESXi hosts using vSphere Lifecycle Management (vLCM), directly from the vSphere interface.

## Requirements

- Your vCenter must be running **vSphere 8** to access the vLCM feature.  
- Make sure the **DRS (Distributed Resource Scheduler)** is enabled in automatic mode.  
- Check that no `.iso` or `.vmdk` files are stored locally on the hosts.

## Instructions

### Step 1: Log in to vSphere

Log in to your vSphere interface and select the **host cluster** you want to update.

### Step 2: Select a new image

1. Go to `Updates > Hosts > Image` to view the current image.  
2. Click **Edit** to change it.  
3. From the dropdown menu, select your desired ESXi version. The first option is usually the latest release from Broadcom.  
4. **OVHcloud recommends using the suggested version** and avoiding downgrades.  
5. Click **Save** to confirm your selection.

### Step 3: Start the update

1. Click **Remediate All** to apply the selected image to all hosts.  
2. This will trigger host maintenance mode. Virtual machines will be moved using **vMotion**.  
3. Make sure no anti-affinity rules block the relocation of VMs.  
4. Click **Start Remediation** to begin the update process.

## Go further

Join our [community of users](/links/community).
