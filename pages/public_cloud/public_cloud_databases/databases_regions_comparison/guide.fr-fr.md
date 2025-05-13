---
title: "Comparison of Public Cloud managed databases Deployment Modes - Understanding 3-AZ / 1-AZ"
excerpt: "Explore OVHcloud's managed databases deployment modes"
updated: 2025-05-23
---

## Objective

OVHcloud offers two deployment modes for its [Public Cloud Databases](/links/public-cloud/databases) service, each tailored to specific needs regarding resilience, availability, performance, and latency. This document provides a detailed explanation of the characteristics of each deployment mode, followed by a comprehensive comparison to help users choose the best option for their requirements.

## Concepts

OVHcloud managed databases offers two main deployment modes, each optimized for specific use cases and offering various levels of redundancy and fault tolerance:

1. **1-AZ Region**:
2. **3-AZ Region**:

## Deployment modes

> [!primary]
>
> The following information pertains to the different deployment modes available in OVHcloud’s managed databases service. Select the mode that best suits your needs based on resilience, availability, and performance.

### 1-AZ Region

#### Infrastructure and Redundancy

A 1-AZ Region consists of a **single availability zone covering multiple data centers within the same region**, utilizing a 2N+1 redundancy design. This setup offers resilience against server and disk failures but may be vulnerable to a complete data center outage. Note that in a 1-AZ region, the databases service is located in a specific data center, and if an outage occurs in the specific data center hosting the databases service, access to data could be impacted, even if other data centers in the zone remain operational.

#### Characteristics

- **Cost-Effectiveness:** Deploying in a 1-AZ region is generally more affordable, making it suitable for development, testing, and non-critical workloads where cost considerations are paramount.
- **Simplified Architecture:** The single-zone setup simplifies deployment and management, reducing complexity for teams that do not require high availability across multiple zones.
- **characteristic:**

#### Limitations

- **Single Point of Failure:** In a 1-AZ region, the databases Engine is deployed within a specific data center. If this data center experiences an outage, access to your databases services could be impacted, even if other data centers within the same availability zone remain operational. 

#### Redundancy Specifications for 1-AZ

| Specification         | Description                                                               |
|-------------------|---------------------------------------------------------------------------|
| **Redundancy Type**   | 2N+1 across multiple data centers                                         |
| **Fault Tolerance**   | Server and disk-level fault tolerance. Data center outage risk .          |
| **Use Case Examples** | Suitable for development, testing, and non-critical databases workloads where cost-effectiveness is prioritized over maximum availability.          |

<a name="3azregion"></a>

### 3-AZ Region

#### Infrastructure and Redundancy

3-AZ Regions consist of **three independent availability zones**, each isolated in terms of power, cooling, and network systems, providing true fault isolation. This architecture ensures **service availability** even if an entire availability zone experiences an outage.

#### Characteristics

- **High Availability:** The databases Engine is deployed across three independent availability zones, ensuring service continuity even if one zone experiences an outage.
- **Fault Tolerance:** With data replicated across all three zones, the system provides robust fault tolerance, minimizing the risk of data loss.
- **Low Latency:** The architecture offers ultra-low latency between availability zones, enhancing performance for databases workloads.

#### Ideal Use Cases

3-AZ Regions are particularly suited to mission-critical and availability-sensitive applications, where data governance requires continuous availability. This includes sectors such as e-commerce, healthcare platforms, financial services or live streaming applications.

#### Performance Specifications for 3-AZ

| Specification         | Description                                                               |
|-------------------|---------------------------------------------------------------------------|
| **Connectivity**      | Low latency between availability zones                                   |
| **High Availability** | Maintains access even in the event of zone failures                                  |
| **Use Case Examples** | Mission-critical and availability-sensitive applications , e-commerce, healthcare platforms, financial services, or live-streaming applications. |

## Go Further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case.

Join our [community of users](/links/community) and visit our [Discord channel](https://discord.gg/ovhcloud).