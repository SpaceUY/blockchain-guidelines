---
title: Compendium
layout: home
nav_order: 2
permalink: /compendium/
---

# Blockchain Compendium

This first section lists some of the most relevant blockchain projects, and their characteristics.

## Ethereum

Ethereum is an open-source blockchain platform, the original proponent of **smart contracts** and **decentralized applications** (dApps).

| Characteristic | Description |
|----------------|-------------|
| **Consensus Mechanism** | [Gasper](https://ethereum.org/developers/docs/consensus-mechanisms/pos/gasper/), Proof of Stake (PoS) since "The Merge" (September 2022) |
| **Virtual Machine/Runtime** | Ethereum Virtual Machine (EVM) |
| **Smart Contract Language** | [Solidity](https://www.soliditylang.org/) |
| **Throughput** | ~15-30 TPS |
| **Block Time** | ~12 seconds |
| **Architecture** | Account-based model with two account types (EOA and Contract Accounts) |
| **Fee Model** | Dynamic fee market ([EIP-1559](https://eips.ethereum.org/EIPS/eip-1559)) with base fee and priority fee |

**Major Updates:**

- **The Merge** (2022): Transition to Proof of Stake
- **Shapella** (2023): Enabled staking withdrawals
- **Dencun** (2024): Proto-Danksharding ([EIP-4844](https://eips.ethereum.org/EIPS/eip-4844)) - blob transactions for L2 scalability
- **Pectra** (2025): Account abstraction improvements ([EIP-7702](https://eips.ethereum.org/EIPS/eip-7702)), validator experience enhancements
- **Fusaka** (2025): [PeerDAS](https://ethereum.org/roadmap/fusaka/peerdas/) to increase blobs per block from 6 to 

**Additional notes:**

- Supports account abstraction through [ERC-4337](https://eips.ethereum.org/EIPS/eip-4337) and [EIP7702](https://eips.ethereum.org/EIPS/eip-7702).

---

## Solana

Solana is a high-performance blockchain platform designed for scalability and speed, featuring unique architectural innovations for parallel transaction processing.

| Characteristic | Description |
|----------------|-------------|
| **Consensus Mechanism** | [Proof of History (PoH)](https://docs.solana.com/cluster/synchronization) + [Tower BFT](https://solana.com/news/tower-bft--solana-s-high-performance-implementation-of-pbft) (PoS) |
| **Virtual Machine/Runtime** | [Sealevel](https://solana.com/news/sealevel---parallel-processing-thousands-of-smart-contracts) - Parallel smart contract runtime |
| **Smart Contract Language** | [Rust](https://www.rust-lang.org/), C, C++ (via LLVM to BPF) |
| **Throughput** | ~3,000-5,000 TPS (mainnet), theoretically up to 65,000 TPS |
| **Block Time** | ~400 milliseconds |
| **Architecture** | [Account model with state decoupling](https://solana.com/docs/core/accounts) - programs (smart contracts) are stateless |
| **Fee Model** | Fixed fee market with [fee payment delegation](https://solana.com/developers/guides/advanced/how-to-request-optimal-compute) support |

**Major Updates:**

- **QUIC Integration** (2023): Improved network layer for better transaction propagation
- **State Compression** (2023): Merkle tree-based compression for NFTs and on-chain data
- **Token Extensions** (2024): Enhanced SPL token standard with confidential transfers, transfer hooks, etc.
- **ZK Compression** (2024): Further compression techniques for reduced state costs
- **Firedancer** (Upcoming): New validator client implementation for improved performance and diversity

**Additional notes:**

- **[Proof of History](https://docs.solana.com/cluster/synchronization)** is a key protocol innovation: a cryptographic clock that allows for deterministic timestamping of events
- Solana has native [account/state decoupling](https://solana.com/docs/core/accounts), making programs **stateless**, and enabling parallel execution
- Transactions can be natively [batched](https://solana.com/docs/core/transactions)
- The [SPL (Solana Program Library)](https://spl.solana.com/) contains standard programs, including tokens
- Supports [Anchor framework](https://www.anchor-lang.com/) for simplified smart contract development
