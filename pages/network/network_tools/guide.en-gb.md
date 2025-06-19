---
title: Using Networking Tools Available to OVHcloud Customers 
excerpt: Find out how to use the networking tools available to OVHcloud customers
updated: 2025-06-20
---

## Objective

OVHcloud provides several tools to customers and prospective customers to test and evaluate their network connectivity with OVHcloud services. In this article, we will cover how to use these tools.

## Topics

- [Looking Glass](#lookingglass)
- [Proof](#proof)
- [Smokeping](#smokeping)
- [Weathermap](#weathermap)


### Looking Glass <a name="lookingglass"></a>

[Looking Glass](https://lg.ovh.net/) is a tool that enables you to run a traceroute or see the routing table to any IP as if you were using a machine in an OVHcloud data center. This tool is perfect if you are a prospective OVHcloud customer or considering expanding your presence to other data centers. It will ensure the networking is sufficient for your needs. The UI is very straightforward.

1. Instructions for the different commands you can run.
2. Select the data center in which you wish to run the test.
3. Select the command you wish to run and the IP/URL to which you want the route.
4. Recent history of your requests to allow you to run them again quickly.


![looking glass](images/networktools1.png){.thumbnail}

### Proof <a name="proof"></a>

[Proof](https://proof.ovh.us/) is a speed test for OVHcloud's network. Proof gives you three options: a generic speed test, arbitrary files to download to test speed, and a proof speed test (allowing you to choose the data center).

![proof](images/networktools2.png){.thumbnail}

When you first go to the site, you will be taken to the **Speedtest** tab. This is a normal speed test. If you click Files, you will be taken to the following page:

![speed test](images/networktools3.png){.thumbnail}

Choose the file size you wish to test and download the file to test your download speed from OVHcloud's network. The final tab is the **Proofs** tab. Select the data center you wish to test from the drop-down menu and you will be taken to the speed test with that data center selected.

![data center selection](images/networktools4.png){.thumbnail}

### Smokeping <a name="smokingping"></a>

[Smokeping](https://smokeping.ovh.net/smokeping) is a monitoring tool to check ICMP reachability, latency, and change in traffic path (traceroute) for external AS/Internal OVH data centers, through FPing, using a sample IP/IPv6 address (added manually).

Smokeping Probe servers are installed in each OVH data center to collect logs.

Once you have accessed the Smokeping tool, you will see a top navigation menu (where a data center can be selected) and a side navigation menu with the following options:

1. **OVH:** Monitors a specific IP address in OVH DC, POP, and OVH Anycast destinations.
2. **ANYCAST:** Global Anycast Destinations like Google DNS and CloudFlare DNS plus destinations from other CDN providers.
3. **EMEA:** Service, content, and/or cloud providers in Europe.
4. **USA / CANADA:** Service, content, and/or cloud providers in the US and Canada.
5. **SA:** Service, content, and/or cloud providers in South America
6. **APAC:** Service, content, and/or cloud providers in Asia / Oceania

![smokeping](images/networking_tools01_.png){.thumbnail}

To view latency results for an entire region, click [code]3. EMEA and then the region name. You can view latency/ping loss for ASN monitored in that specific region.

![latency results](images/networking_tools02_.png){.thumbnail}

You can use the search box in the upper-right corner to check results for a specific AS/Name. Any results will be displayed on the left side of the page.

![ASN](images/networking_tools03_.png){.thumbnail}

If you click the name of the provider in the search results, you will see historical latency and traceroute results, for up to the last year.

![Historical results](images/networking_tools04_.png){.thumbnail}

### Weathermap <a name="weathermap"></a>

The [OVHcloud weathermap](https://weathermap.ovh.net/) is a way to view the network backbone. Here you can view the percentage of traffic load on each link.

1. Data center selection
2. Search boxes and adjust the time period
3. Load scale legend
4. Navigation tips
5. See link details

![weathermap](images/networking_tools05_.png){.thumbnail}

For more information and tutorials, please see our other [Networking and Security support guides](/products/network) or explore the [guides for other OVHcloud products and services](https://help.ovhcloud.com/csm/en-gb-documentation?id=kb_home).

## Go further

Join our [community of users](/links/community).
