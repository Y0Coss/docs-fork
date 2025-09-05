---
title: Concepts overview
excerpt: 'Concepts overview - OVHcloud Connect'
updated: 2025-09-04
---

## What is OVHcloud Connect?

OVHcloud Connect is a private, dedicated connection between your on-premises network and your OVHcloud vRack. It is designed to extend your network and securely connect to your cloud resources, bypassing the public internet.

![OVHcloud Connect](images/VrackConnectDedicated.png){.thumbnail}

## Benefits of OVHcloud Connect

### Dedicated service

Dedicated Mode is a direct connection with OVHcloud devices. You can manage different configurations, from a single connection to a multiple one using LACP (Layer 2) or BGP-ECMP (Layer 3) with port speed at 1Gb or 10Gb. Interface and bandwidth are not shared with other customers.

### Private connection

Your traffic is isolated from the Internet. You manage your own VLANs (Layer 2) and/or your own IP addresses (Layer 3). BGP instances are private, and you can configure the ASN you want.

OVHcloud Connect is connected to your vRack with all compatible services.

### Network extension

OVHcloud Connect can be connected either to your WAN or your data centre network, allowing seamless extension to the cloud. This eases hybrid cloud strategies and migrations by keeping your existing VLAN topology or IP addresses.

### High availability

Using BGP, you can interconnect your network through multiple Points-of-Presence (PoPs) and reach several OVHcloud data centres. From your vRack, you can configure BGP to enable maximum resiliency with distributed services.

## Components of OVHcloud Connect

### PoP - EntryPoint

Points of presence are facilities like Equinix, InterXion, Telehouse or Global Switch. The OVHcloud Connect service entry PoP is called *EntryPoint*.

### DC - EndPoint

The OVHcloud data centre is the service *EndPoint* of OVHcloud Connect.

### Cross-connect

A cross-connection is a physical link (monomode fiber) managed by the local facility team in the PoP. The cross-connection is established in the MMR (Meet-Me Room) between the position given by OVHcloud and the position owned by the customer. The customer must order and manage the cross-connect for OVHcloud Connect Direct. 

### vRack

The OVHcloud Private Network, available on compute resources between all OVHcloud data centres. It allows you to connect compatible services into a single private network.

### BGP

BGP (Border Gateway Protocol) is the routing protocol used in Layer 3 mode to manage routes between your network and the OVHcloud vRack.

## Principles of OVHcloud Connect

OVHcloud Connect is based on a virtual link between an *EntryPoint* and an *EndPoint*. The *EntryPoint* is where you want to make the interconnection with OVHcloud. The *EndPoint* is the OVHcloud data centre with your services. You can choose any data centre in the same region as the PoP. 

### Layer 2 Mode (L2)

The virtual link is a L2 tunnel for OVHcloud Connect L2. Only one PoP/*EntryPoint* with one DC/*EndPoint* can be configured.

### Layer 3 Mode (L3)

The virtual link is a full mesh IP network between any PoP/*EntryPoint* and any DC/*EndPoint* of the same region.

## Accessible PoPs per provider

The OVHcloud Points of Presence (PoPs) available through each of our cloud service provider partners are outlined in the following list:

| Provider | OVHcloud Connect PoPs |
| :--- | :--- |
| **OVHcloud Connect Direct** | **Europe:** Lille (*ETIX - ETX2*), Paris (*Equinix - PA3, GlobalSwitch, Telehouse - TH2*), Frankfurt (*Equinix - FR5*), Warsaw (*Equinix - WA2*), Madrid (*Digital Realty - MAD2*), London (*Equinix - LD5, Telehouse - West*) <br> **North America:** Montreal (*Cologix - MTL3*), Toronto (*Equinix - TR1*), Washington (Ashburn) (*Equinix - DC10*), Seattle (*Westin Building - WBX*) <br> **APAC:** Mumbai (*Equinix - MB2*), Singapore (*Equinix - SG1*) |
| **Console Connect** | **Europe:** Paris (*Equinix - PA3, Telehouse - TH2*), Frankfurt (*Equinix - FR5*), London (*Equinix - LD5*) <br> **North America:** Montreal (*Cologix - MTL3*), Seattle (*Westin Building - WBX*), Toronto (*Equinix - TR1*), Washington (Ashburn) (*Equinix - DC10*) <br> **APAC:** Singapore (*Equinix - SG1*) |
| **Digital Realty** | **Europe:** Paris (*Telehouse - TH2*), Madrid (*Digital Realty - MAD2*) <br> **North America:** Seattle (*Westin Building - WBX*) |
| **Equinix** | **Europe:** Paris (*Equinix - PA3*), Frankfurt (*Equinix - FR5*), London (*Equinix - LD5*) <br> **North America:** Toronto (*Equinix - TR1*), Washington (Ashburn) (*Equinix - DC10*) <br> **APAC:** Singapore (*Equinix - SG1*) |
| **InterCloud** | **Europe:** Paris (*Equinix - PA3, GlobalSwitch, Telehouse - TH2*) |
| **Megaport** | **Europe:** Paris (*Equinix - PA3*), Frankfurt (*Equinix - FR5*), London (*Equinix - LD5*) <br> **North America:** Washington (Ashburn) (*Equinix - DC10*) |
| **Orange** | **Europe:** Paris (*Equinix - PA3, Telehouse - TH2*) |
| **RISQ** | **North America:** Montreal (*Cologix - MTL3*) |

## Accessible Regions per PoP

For a given PoP, OCC can be connected to specific regions. Here is the list of connectable regions depending on the selected PoP:

| OVHcloud Connect PoPs | Accessible OVHcloud Regions |
| :--- | :--- |
| **Europe**<br>Paris: Equinix - PA3, GlobalSwitch, Telehouse - TH2<br>Frankfurt: Equinix - FR5<br>London: Equinix - LD5, Telehouse - West<br>Madrid: Digital Realty - MAD2<br>Warsaw: Equinix - WA2<br>Lille: ETIX - ETX2 | **Europe**<br>Strasbourg (`eu-west-sbg`),<br>Gravelines (`eu-west-gra`),<br>Roubaix (`eu-west-rbx`),<br>Paris (`eu-west-par`),<br>Limburg (`eu-west-lim`),<br>Warsaw (`eu-central-waw`),<br>Erith (`eu-west-eri`) |
| **North America**<br>Montreal: Cologix - MTL3<br>Toronto: Equinix - TR1 | **North America**<br>Beauharnois (`ca-east-bhs`),<br>Toronto (`ca-east-tor`) |
| **Asia-Pacific**<br>Singapore: Equinix - SG1<br>Mumbai: Equinix - MB2 | **Asia-Pacific**<br>Singapore (`ap-southeast-sgp`),<br>Mumbai (`ap-south-mum`) |

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our community of users on <https://community.ovh.com/en/>.
