---
title: Concepts - Primary IP or Additional IP
excerpt: Understand the differences between Primary IP and Additional IP addresses and their uses
updated: 2025-07-25
---

## Objective

Infrastructure resources can be exposed to the Internet via their own public IP addresses. For services created on such an infrastructure it is however not recommended to use these IP addresses to expose services themselves.

When a service should be optimised for scalability or agility, its public IP address should not be linked to a particular server or virtual machine. For such cases, separate reserved IP addresses are the best way to make services publicly available.

In the Bare Metal universe, you can use the Primary IP addresses of your services, or configure Additional IP addresses, which provide a flexible way to manage public access to your services. They can stay infrastructure-agnostic and be scaled up or migrated whenever needed.

## IP Addresses in OVHcloud: Primary, Additional, and Floating

OVHcloud offers various types of IP addresses, each designed for specific use cases and offering different levels of flexibility and functionality. Understanding the distinctions between Primary IP, Additional IP, and Floating IP is crucial for effective network management and service deployment.

## Primary IP Addresses

Primary IP addresses are fundamental to OVHcloud services, providing immediate connectivity and reachability upon service deployment.

### Characteristics:

* **Pre-configured:** Typically provided with a cloud service and comes pre-configured, simplifying initial setup.
* **Purpose:** Its main purpose is to enable easy communication and ensure reachability for the associated service.
* **Availability:** Both IPv4 and IPv6 primary addresses are available with many OVHcloud products. Refer to specific product pages for detailed availability.
* **Configuration:** IPv4 and IPv6 address configuration details, such as address, prefix size, or default gateway, can be found within the OVHcloud Control Panel, usually in the Network tab of the given product.

### Use Cases:

* Default network interface for a server or service.
* Basic connectivity and management access.

### Related Guides:
- [Configuring IPv6 on dedicated servers](/pages/bare_metal_cloud/dedicated_servers/network_ipv6)

## Additional IP Addresses

Additional IP addresses offer enhanced flexibility and are infrastructure-agnostic, meaning they are not tied to any specific underlying hardware or solution. This allows for dynamic reassignment between different services within the same region.

### Characteristics:

* **Flexibility:** Offers greater flexibility compared to Primary IPs.
* **Infrastructure-Agnostic:** Not tied to specific hardware, allowing dynamic reassignment.
* **Dynamic Reassignment:** Can be dynamically reassigned between different services within the same region.
* **Availability:**
    * **IPv4:** Can be used with multiple products.
    * **IPv6:** Supports Additional IPv6 when used with vRack.

### Attachment Methods:

Additional IP addresses can be attached to OVHcloud services in two primary ways (availability may vary):

1.  **Via Public Interface:**
    * Available for Additional IPv4 only.
    * An Additional IPv4 address (or a block of addresses) can be used similarly to the Primary IP of a server.
    * Refer to your product’s specifications for network/gateway setting details.

2.  **Via vRack Private Network:**
    * Supports both Additional IPv4 and Additional IPv6.
    * Available for products compatible with vRack.
    * **Advantages of using with vRack:**
        * **Crossing Regional Boundaries:** While Additional IP addresses can only be moved between products within the region they were issued, using them over a vRack allows customers to define the gateway region (where public traffic enters and leaves the vRack network), while backend services can be utilized in any location that supports vRack network.
        * **IPv6 Subnet Routing:** This feature is available only for Additional IPv6 when used over a vRack network, enabling more granular control over IPv6 traffic within your private network.

### Use Cases:

**Failover**: Quickly reassign IP addresses to backup services in case of main services failure;
**Load Balancing**: Configure an OVHcloud Load Balancer, and distribute traffic among several servers or clusters;
**IP aliasing**: Assign several IP addresses to the same network interface, and host multiple websites or services on a single server;

### Related Guides:
- [Configuring an Additional IPv6 block in a vRack](/pages/bare_metal_cloud/dedicated_servers/configure-an-ipv6-in-a-vrack)
- [Configuring an Additional IP block in a vRack](/pages/bare_metal_cloud/dedicated_servers/configuring-an-ip-block-in-a-vrack)
- [Moving an Additional IP](/pages/bare_metal_cloud/dedicated_servers/move-failover-ip)
- [Configuring Additional IPs in bridge mode on your virtual machines](/pages/bare_metal_cloud/dedicated_servers/network_bridging)

## Go further

Join our [community of users](/links/community).