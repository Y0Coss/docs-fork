---
title: "How to configure the Anti-DDos Infrastructure for Solana"
excerpt: "Learn how to leverage the OVHcloud Anti-DDoS infrastructure to protect your Solana nodes without blocking their functionality"
updated: 2025-09-01
---

## Objective

This guide's objective is to help you better understand our anti-DDoS Infrastructure, and to provide instructions on how to configure effective protection without harming legitimate network traffic relative to the Blockchain.

## Requirements

TBD

## Introduction to Blockchain

Blockchain is a decentralized, distributed digital ledger that records transactions across many computers, ensuring that the data cannot be altered retroactively without the alteration of all subsequent blocks and the consensus of the network.

This technology creates a tamper-proof and transparent record of information, such as financial transactions, making it secure and trustworthy.

In some cases, communication spikes can trigger our Anti-DDoS Infrastructure, and lead to the detection of some traffic patterns as false positives. 

## Instructions

To avoid having your network traffic blocked by the Anti-DDoS Infrastructure due to false positives, we strongly recommend to list your nodes IP addreesses, and report them to our support teams. This way, they will be able to create a custom Solana profile that will tune the protection to your infrastructure and allow uninterrupted functionality. You can use [this form](link_to_be_determined) to report your nodes list. 

At the moment, there is no direct way for users to circumvent this issue without contacting OVHcloud support.

If you are not sure about which elements you should send to our teams, you can refer to the following use cases.

### Use Case : Solana

Solana is a high-performance blockchain platform known for its exceptional speed and low transaction costs, making it a popular alternative for decentralized applications. It achieves this by using a unique cryptographic clock called Proof of History (PoH), which timestamps transactions to enable parallel processing and greater efficiency. This system is paired with a Proof of Stake (PoS) consensus mechanism, where validators are chosen based on their staked SOL, ensuring the network remains secure and decentralized. 

Solana's architecture also utilizes a combination of protocols like Tower BFT, Turbine, Gulf Stream and Sealevel to optimize block propagation, transaction processing, and smart contract execution, all contributing to its high speed and efficiency.

Solana uses the following network protocols and ports:

| Protocol | Usage | Port |
| :--- | :--- | :--- |
| Gossip | Node discovery and cluster info sharing | TCP/UDP 8000-10000 (default 8001) |
| Turbine | Network state dissemination and block/shred propagation | TCP/UDP 8000-10000 (default 8003) |
| JSON-RPC over HTTP | Used by applications to query the blockchain and submit transactions | TCP 8899 |
| JSON-RPC WebSockets API | Used by applications to query the blockchain and submit transactions | TCP 8900 |
| QUIC | Ingest transactions from clients, improving network reliability and efficiency | UDP 8000-8002 (may vary) |


## Go further

Join our [community of users](/links/community).
