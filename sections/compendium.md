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

## Sui

Sui is a Layer 1 blockchain built with an object-centric data model and the Move programming language, designed for horizontal scalability and low-latency transactions.

| Characteristic | Description |
|----------------|-------------|
| **Consensus Mechanism** | [Mysticeti](https://docs.sui.io/concepts/sui-architecture/consensus#mysticeti) - High-throughput BFT consensus (PoS) |
| **Virtual Machine/Runtime** | [Move VM](https://docs.sui.io/concepts/sui-move-concepts) with [object-centric execution model](https://docs.sui.io/concepts/object-ownership) |
| **Smart Contract Language** | [Sui Move](https://docs.sui.io/concepts/sui-move-concepts) - Object-centric variant of Move |
| **Throughput** | ~5,000-20,000 TPS (observed), theoretically 100,000+ TPS |
| **Block Time** | ~400-500ms finality |
| **Architecture** | [Object-based model](https://docs.sui.io/concepts/object-ownership) with owned, shared, and immutable objects |
| **Fee Model** | Gas-based with [sponsored transactions](https://docs.sui.io/concepts/transactions/sponsored-transactions) and [gas smashing](https://docs.sui.io/concepts/transactions/gas-smashing) |

**Major Updates:**

- **Mainnet Launch** (May 2023): Initial mainnet deployment
- **Mysticeti Consensus** (2024): New consensus protocol with sub-second finality
- **GraphQL Support** (2024): Enhanced querying capabilities for dApps
- **zkLogin** (2024): [Zero-knowledge proofs for authentication](https://docs.sui.io/concepts/cryptography/zklogin) via OAuth providers
- **DeepBook v3** (2024): Native on-chain order book for DeFi
- **Walrus Protocol** (2024): Decentralized storage and data availability layer

**Additional notes:**

- **[Object-centric model](https://docs.sui.io/concepts/object-ownership)** enables **causally ordered transactions** - simple transactions bypass consensus entirely for instant finality
- **[Sui Move](https://docs.sui.io/concepts/sui-move-concepts)** extends Move with object ownership semantics, enabling true digital asset representation
- **[Parallel execution](https://docs.sui.io/learn/how-sui-works)** through object ownership model - transactions affecting different objects execute in parallel
- **[zkLogin](https://docs.sui.io/concepts/cryptography/zklogin)** enables Web2-style onboarding with cryptographic privacy
- Native support for [programmable transaction blocks](https://docs.sui.io/concepts/transactions/prog-txn-blocks) (PTBs) for complex composable operations
- [Kiosk standard](https://docs.sui.io/standards/kiosk) for creator royalty enforcement and transfer policies

---

## Hedera

Hedera is a Layer 1 distributed ledger platform built on hashgraph consensus, offering enterprise-grade performance with unique governance and native services.

| Characteristic | Description |
|----------------|-------------|
| **Consensus Mechanism** | [Hashgraph](https://hedera.com/learning/hedera-hashgraph/what-is-hashgraph-consensus) - Asynchronous Byzantine Fault Tolerant (aBFT) consensus (PoS) |
| **Virtual Machine/Runtime** | [EVM-compatible](https://docs.hedera.com/hedera/smart-contracts) with a suite of native services |
| **Smart Contract Language** | [Solidity](https://www.soliditylang.org/) (full EVM compatibility) |
| **Throughput** | ~10,000 TPS (network capacity), low and predictable fees |
| **Block Time** | ~3-5 seconds finality |
| **Architecture** | Directed Acyclic Graph (DAG) based, not a traditional blockchain - data is stored in cryptographically linked files |
| **Fee Model** | Fixed, low-cost fee structure denominated in USD but paid in HBAR |

**Major Updates:**

- **Mainnet Launch** (September 2019): Initial mainnet deployment
- **HCS 2.0** (2021): Enhanced [Hedera Consensus Service](https://docs.hedera.com/hedera/sdks-and-apis/sdks/consensus-service) capabilities
- **Smart Contracts 2.0** (2022): Full EVM equivalence with improved performance
- **Token Service v2** (2023): Enhanced [HTS features](https://docs.hedera.com/hedera/sdks-and-apis/sdks/token-service) including custom fees and royalties
- **Staking** (2023): Native proof-of-stake staking mechanism
- **EVM Compatibility Updates** (2024): Continued improvements for Ethereum developer experience

**Additional notes:**

- **[Hashgraph consensus](https://hedera.com/learning/hedera-hashgraph/what-is-hashgraph-consensus)** provides **aBFT (asynchronous Byzantine Fault Tolerant)** security - the highest level of security for distributed systems
- **[Governed by a council](https://hedera.com/council)** of diverse global organizations (Google, IBM, Boeing, Deutsche Telekom, etc.) preventing centralized control
- **Native Services** beyond smart contracts:
  - [HCS (Hedera Consensus Service)](https://docs.hedera.com/hedera/sdks-and-apis/sdks/consensus-service): Decentralized ordering and timestamping
  - [HTS (Hedera Token Service)](https://docs.hedera.com/hedera/sdks-and-apis/sdks/token-service): Native token creation without smart contracts
  - [HFS (Hedera File Service)](https://docs.hedera.com/hedera/sdks-and-apis/sdks/file-service): Decentralized file storage
- **Fixed fee structure** makes costs predictable for enterprise applications
- Full **EVM compatibility** allows easy migration of Ethereum dApps

---

