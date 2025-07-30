---
title: "Public VCF as-a-Service - Linking a public IP block with vRack for VCD"
excerpt: "Find out how to link the public IP address block delivered with your VCD organization and its vRack"
updated: 2025-07-30
---

<style>
.w-640 {
  max-width:640px !important;
}
</style>

## Objective

When you order a new VCD organization, a vRack is delivered to you, along with a block of public IP addresses.

This IP block is not directly linked to your vRack. You will need to link it manually.

**Find out how to link the public IP address block delivered with your VCD organization and its vRack.**

## Requirements

- A [Public VCF as-a-Service](/links/hosted-private-cloud/vmware-vcd) on OVHcloud solution.
- Being the technical administrator of the managed [VMware vSphere on OVHcloud](/links/hosted-private-cloud/vmware) infrastructure.
- Access to the [OVHcloud Control Panel](/links/manager)

## Instructions

1. Log in to your [OVHcloud Control Panel](/links/manager)
2. Display the VCD organization information from the `Managed VCD`{.action} menu in the left-hand column, then select your organization.

![Managed VCD organization](images/01-vcd-link-ip-vrack.png){.thumbnail .w-640}

3. From the `General information`{.action} tab, the vRack attached to your organization will appear with an ID in the form `pn-xxxxxxx`.

![VCD vRack attached](images/02-vcd-link-ip-vrack.png){.thumbnail .w-640}

4. In the left-hand column, in the `Network`{.action} menu, select your vRack `pn-xxxxxxx`.

![Network vRack](images/03-vcd-link-ip-vrack.png){.thumbnail .w-640}

5. Select the IP block to link to your vRack/Organization and click `Add`{.action}.

![add IP to vRack](images/04-vcd-link-ip-vrack.png){.thumbnail .w-640}

## Go further

If you need training or technical assistance to implement our solutions, please contact your Technical Account Manager or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Ask questions, give your feedback and interact directly with the team building our Hosted Private Cloud services on the dedicated [Discord](https://discord.gg/ovhcloud) channel.

Join our [community of users](/links/community).