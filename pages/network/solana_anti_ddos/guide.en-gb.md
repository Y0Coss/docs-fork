---
title: "How to configure the Anti-DDos Infrastructure for Solana"
excerpt: "Learn how to leverage the OVHcloud Anti-DDoS infrastructure to protect your Solana nodes without blocking their functionality"
updated: 2025-09-01
---

## Objective

This guide's objective is to help you better understand our anti-DDoS Infrastructure and to provide instructions on how to configure effective protection.

## Requirements

TBD

## Introduction to Solana

Blockchain is a decentralized, distributed digital ledger that records transactions across many computers, ensuring that the data cannot be altered retroactively without the alteration of all subsequent blocks and the consensus of the network. 
This technology creates a tamper-proof and transparent record of information, such as financial transactions, making it secure and trustworthy.

Solana is a high-performance blockchain platform known for its exceptional speed and low transaction costs, making it a popular alternative for decentralized applications. It achieves this by using a unique cryptographic clock called Proof of History (PoH), which timestamps transactions to enable parallel processing and greater efficiency. This system is paired with a Proof of Stake (PoS) consensus mechanism, where validators are chosen based on their staked SOL, ensuring the network remains secure and decentralized. Solana's architecture also utilizes a combination of protocols like Tower BFT, Turbine, Gulf Stream and Sealevel to optimize block propagation, transaction processing, and smart contract execution, all contributing to its high speed and efficiency.

Solana uses the following network protocols and ports:

Validator-to-Validator Communication:

&bull; Protocols : Gossip and Turbine are used for network state dissemination and block propagation.

&bull; Ports : UDP 8000-10000 (dynamic range).

Client-to-Node Communication (RPC API):

&bull; Protocol : JSON-RPC over HTTP and WebSockets is used for applications to query the blockchain and submit transactions.

&bull; Ports : 
- JSON-RPC HTTP API : TCP 8899
- WebSockets API : TCP 8900.

Transaction Ingestion:

&bull; Protocol : QUIC is used to ingest transactions from clients, improving network reliability and efficiency.

&bull; Ports : UDP 8000-8002 (may vary)

## Instructions

In some cases, communication spikes can trigger our Anti-DDoS Infrastructure and lead to the detection of traffic patterns as false positives.

To avoid this, we strongly recommend to list your HTTP and WebSocket nodes IP addreesses, and report them to our support teams. This way, they will be able to create a custom Solana profile that will tune the protection to your infrastructure and allow uninterrupted functionality. You can use [this form](link_to_be_determined) to report your nodes list. 

At the moment, there is no direct way for users to circumvent this issue without contacting OVHcloud support.

## Go further

Join our [community of users](/links/community).
