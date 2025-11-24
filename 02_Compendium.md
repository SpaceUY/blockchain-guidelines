---
title: Compendium
layout: home
nav_order: 2
permalink: /compendium/
---

# Blockchain Compendium

This first section lists some of the most relevant blockchain projects, and their characteristics.

## Ethereum

Ethereum is an open-source Layer-1 blockchain platform, the original proponent of **smart contracts** and **decentralized applications** (dApps).

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

Solana is a high-performance Layer 1 blockchain platform designed for scalability and speed, featuring unique architectural innovations for parallel transaction processing.

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

---

## Aptos

Aptos is a Layer 1 blockchain focused on safety, scalability, and upgradeability.

| Characteristic | Description |
|----------------|-------------|
| **Consensus Mechanism** | [AptosBFT](https://aptos.dev/en/network/blockchain/blockchain-deep-dive#consensus) - Byzantine Fault Tolerant consensus (PoS) based on [HotStuff](https://github.com/asonnino/hotstuff) |
| **Virtual Machine/Runtime** | [Move VM](https://aptos.dev/en/build/smart-contracts) with [Block-STM](https://aptos.dev/en/network/blockchain/blockchain-deep-dive#parallel-execution) for parallel execution |
| **Smart Contract Language** | [Move](https://move-language.github.io/move/) - Resource-oriented programming language |
| **Throughput** | ~10,000-160,000 TPS (theoretical), ~4,000-7,000 TPS (observed) |
| **Block Time** | Sub-second finality (~300-500ms) |
| **Architecture** | Account-based model with resource-oriented design |
| **Fee Model** | Gas-based fee market with [gas fee delegation](https://aptos.dev/en/build/guides/aptos-gas) |

**Major Updates:**

- **Mainnet Launch** (October 2022): Initial mainnet deployment
- **Token Standard v2** (2023): Enhanced fungible and non-fungible token standards
- **Keyless Accounts** (2024): [Blockchain-native OAuth](https://aptos.dev/en/build/guides/aptos-keyless) for seamless onboarding
- **Randomness API** (2024): On-chain verifiable randomness
- **Fungible Assets** (2024): New flexible token standard
- **Passkey Support** (2024): WebAuthn integration for improved UX

**Additional notes:**

- **[Move language](https://move-language.github.io/move/)** provides resource safety through linear types, preventing common vulnerabilities like double-spending
- **[Block-STM](https://aptos.dev/en/network/blockchain/blockchain-deep-dive#parallel-execution)** enables **optimistic parallel transaction execution** with **automatic conflict detection**
- Native [multisig support](https://aptos.dev/en/build/guides/build-e2e-dapp/3-add-wallet-support#multi-agent-transactions) and transaction sponsorship
- Focus on formal verification and security through Move's design
- Supports [Aptos Standards](https://aptos.dev/en/build/smart-contracts/aptos-standards) for tokens, NFTs, and digital assets

---

