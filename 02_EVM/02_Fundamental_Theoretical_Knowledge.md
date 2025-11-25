---
title: Fundamental Theoretical Knowledge
layout: home
parent: Ethereum Virtual Machine
permalink: /evm/fundamentals
nav_order: 2
---

# Fundamental Theoretical Knowledge

---

- **Cryptography**

  - Asymmetric cryptography: Properties (authenticity, non-repudiation, non-reusability)

    - [Public Key Cryptography - Computerphile](https://www.youtube.com/watch?v=GSIDS_lvRv4)

  - Elliptic Curves: Addition and Multiplication Operation, secp256k1 curve

    - [Elliptic Curve Diffie Hellman](https://www.youtube.com/watch?v=F3zzNa42-tQ)

      - Elliptic curves (0:00 - 9:00)

      - Diffie Hellman (9:00 - 11:55) -> How to exchange a secret

    - [Elliptic Curves](https://docs.google.com/document/u/0/d/17RIfXlziCN3j5ST0eM0SsO5E-5Q2OJVqAn37TCy3A2s/edit)

  - Asymmetric cryptography on elliptic curves:

    - [https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages](https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages)

      ((r,s,v), Digital signature, Signature verification, Recovery)

    - [https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md)

  - Signature malleability problem:

    - [https://www.youtube.com/shorts/RqOaaglSqlI](https://www.youtube.com/shorts/RqOaaglSqlI)

  - Extra: have fun with [Cryptohack!](https://cryptohack.org/)

  - Exercises on [02_fundamentals/src/cryptography](https://github.com/SpaceUY/blockchain-techbook/tree/main/src/02-fundamentals/cryptography)

---

- **HD Wallets**

  - [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki), [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki), [BIP44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)

    - [Blockchain tutorial 28: Bitcoin Improvement Proposal 39 (BIP-39) mnemonic words](https://www.youtube.com/watch?v=hRXcY_tIlrw)

    - [Blockchain tutorial 29: Hierarchical Deterministic wallet - BIP32 and BIP44](https://www.youtube.com/watch?v=2HrMlVr1QX8)

    - [https://tara-annison.medium.com/mnemonic-seed-phrases-bip39-6b843291834c](https://tara-annison.medium.com/mnemonic-seed-phrases-bip39-6b843291834c)

    - Understand in general terms the motivation for the standards mentioned.

    - Master private key and Master public key [https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/](https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/)

    - Child Key derivation [https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/#child-key-derivation](https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/#child-key-derivation)

    - Exercises on [02_fundamentals/src/hd-wallets](https://github.com/SpaceUY/blockchain-techbook/tree/main/src/02-fundamentals/hd-wallets)

---

- **EOA vs IOA**

  - [Introduction To Ethereum](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pages 15 to 20 [Author David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))

  - [https://ethereum.org/en/developers/docs/accounts/](https://ethereum.org/en/developers/docs/accounts/)

  - [Ethereum Accounts Explained: Smart Contract vs Externally Owned Account (EOA)](https://www.youtube.com/watch?v=CbV3jrhj-Os&t=106s)

  - [Practical Exercise](https://colab.research.google.com/drive/1E8r0wHjeixSLifFXmoc0COP1-pjYSPcd#scrollTo=WSWBi6kVp7bc)

---

- **Blockchain**

  - Block, content, tree root (state, transactions, receipts)

    - [Introduction To Ethereum](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pages 32 to 40 [Author David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))

    - [https://ethereum.org/en/developers/docs/blocks/](https://ethereum.org/en/developers/docs/blocks/)

    - [Simplified interactive view of a blockchain](https://andersbrownworth.com/blockchain/hash)

    - [Blockchain Demo](https://andersbrownworth.com/blockchain/)

  - Transactions

    - [Introduction To Ethereum](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pages 27 to 31 [Author David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit)) (Message Calls, Contract Creations)

    - [https://ethereum.org/en/developers/docs/transactions/](https://ethereum.org/en/developers/docs/transactions/)

    - Extra
      - [Step by step tx](https://www.notonlyowner.com/learn/que-pasa-cuando-envias-un-dai)

  - Gas

    - [Introduction To Ethereum](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pág 22 a 27 [Author David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit)) (Gas, GasLimit, Gas Price, OOG)

    - [https://ethereum.org/en/developers/docs/gas/](https://ethereum.org/en/developers/docs/gas/)

    - [Can ETH Become DEFLATIONARY? EIP 1559 Explained](https://www.youtube.com/watch?v=MGemhK9t44Q)

  - [Blockchain Transactions Deep Dive: Análisis, Costos y más con Germán Küber](https://www.youtube.com/watch?v=FrCyT_FSdjQ)

    - Executing a transaction

    - Gas costs (different types: reads, writes)

    - Gas refund when clearing values ​​in storage

---

- **JSON - RPC (Eth API)**

  - [https://ethereum.org/en/developers/docs/apis/json-rpc/](https://ethereum.org/en/developers/docs/apis/json-rpc/)

  - [https://ethereum.github.io/execution-apis/api-documentation/](https://ethereum.github.io/execution-apis/api-documentation/)

  - [https://stackoverflow.com/questions/50985798/difference-between-sendtransaction-and-sendrawtransaction-in-web3-py](https://stackoverflow.com/questions/50985798/difference-between-sendtransaction-and-sendrawtransaction-in-web3-py) (Diferencia between eth_sendTransaction and eth_sendRawTransaction)

  - Exercise

        -   [Playground](https://ethereum-json-rpc.com/). Play around with some of the following:

    eth_chainId, eth_blockNumber, eth_gasPrice, eth_maxPriorityFeePerGas, eth_getBalance, eth_getCode, eth_call, eth_estimateGas, eth_getBlockByNumber, eth_getBlockByHash, eth_getTransactionByHash, eth_getTransactionReceipt.

---

- **Blockchain Storage**

  - [Storage In Ethereum](https://drive.google.com/open?id=1uJpX04AV36ffxKn-VWPJYhYe9U1lt34_) ([Author David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))

  - Extra: [Merkle Trees Visualization](https://blockchain-academy.hs-mittweida.de/merkle-tree/)

  - Practical Exercise

---

- **EVM (Ethereum Virtual Machine)**

  - [8_EVM - Ethereum Virtual Machine.pdf](https://drive.google.com/open?id=1dmQvvK8MGQdPwgtDX7SxExRcNnKa-ygU) ([Author David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))

  - [EVM (First Part) | Live advanced workshop with Germán Küber](https://www.youtube.com/watch?v=hT6IxwGr8hs) (Smart contract bytecode, opcods, EVM)

  - Practical Exercise

    - See how a solidity code is executed using [https://www.evm.codes/playground](https://www.evm.codes/playground)

  - Extra: [https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015](https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015)

---

- **Nodes and Clients**

  - [https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/](https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/) (Ethereum consensus and execution client)

  - [https://ethereum.org/en/developers/docs/nodes-and-clients/light-clients/](https://ethereum.org/en/developers/docs/nodes-and-clients/light-clients/) (Light nodes)

---

- **Consensus Algorithms**

  - The Byzantine Generals' Problem

    - [Distributed Systems 2.2: The Byzantine generals problem](https://www.youtube.com/watch?v=LoGx_ldRBU0)

    - Extra: [Two Generals' Problem Explained](https://www.youtube.com/watch?v=s8Wbt0b8bwY)

  - [https://ethereum.org/en/developers/docs/consensus-mechanisms/](https://ethereum.org/en/developers/docs/consensus-mechanisms/)

  - [Understanding Blockchain Consensus Mechanisms](https://www.youtube.com/watch?v=ojxfbN78WFQ)

  - PoW

    - [https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/)

      - [What is Proof of Work (PoW)｜ Explained For Beginners](https://www.youtube.com/watch?v=3EUAcxhuoU4)

  - PoS

    - [What is staking and proof of stake? Basic explanation](https://www.youtube.com/watch?v=bQYExyRc14M)

  - PoS in Ethereum

    - [Future-block MEV in Proof of Stake by Torgin Mackinga - Devcon Bogotá](https://www.youtube.com/watch?v=rnR7puADz-o)

    - [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos)

    - [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#transaction-execution-ethereum-pos](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#transaction-execution-ethereum-pos)

    - [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/block-proposal/](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/block-proposal/)

    - [https://ethereum.org/en/developers/docs/networking-layer/#connecting-clients](https://ethereum.org/en/developers/docs/networking-layer/#connecting-clients)

    - Extra:

      - [Updates on Proposer-Builder Separation by Barnabé Monnot - Devcon Bogotá](https://www.youtube.com/watch?v=sQQ2UYB3qOI)

      - [$25,000,000 USD MEV Boost Hack Explained Live!](https://www.youtube.com/watch?v=Mlj2PFTDSGI)

  - PoA

    - [https://ethereum.org/en/developers/docs/consensus-mechanisms/poa/](https://ethereum.org/en/developers/docs/consensus-mechanisms/poa/)

---

- **Meta txs**

  - Forwarder, EIP712, ERC2771 (Context y Forwarder)

  - Reply attack protection (Nonce nativo vs “Nonce artificial”)

---

- **Upgradeability Patterns**

  - Conceptually and its benefits: Transparent, UUPs, Beacon, Diamond, [Proxies, Beacons & Diamond Pattern - EVM Expeditions #02 - byterocket](https://www.youtube.com/watch?v=iXLoSVcVhUg)

  - Practical Exercise:

    - Looking at [Etherscan](https://etherscan.io), go to an upgradeable contract, identify which is the implementation, which is the proxy, how to invoke a read, write..

---

- **Specific Domain (NFTs)**

  - NFTs ([ERC721](https://docs.openzeppelin.com/contracts/2.x/api/token/erc721), [ERC1155](https://docs.openzeppelin.com/contracts/3.x/erc1155)).

  - NFT metadata standard

    - [What is IPFS and How Does it Work?](https://www.youtube.com/watch?v=z2judsbo-5E)

    - [https://docs.opensea.io/docs/metadata-standards](https://docs.opensea.io/docs/metadata-standards)

  - Practical Exercise

    - Using [Remix](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null) deploy [ERC721](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol) and [ERC1155](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC1155/ERC1155.sol). Metadata can be uploaded to IPFS by watching the following video [05. Upload your art and metadata to IPFS with Pinata.cloud](https://www.youtube.com/watch?v=mSUpcZA5o0). Mint NFTs and use the methods balanceOf, approve, transferFrom etc.. to have as complete an understanding as possible.

---

- **Specific Domain (DeFi)**

  - [ERC20](https://docs.openzeppelin.com/contracts/2.x/api/token/erc20)

  - Liquidity Pool & AMM

    - [What is an Automated Market Maker? (Liquidity Pool Algorithm)](https://www.youtube.com/watch?v=1PbZMudPP5E)

    - [How do LIQUIDITY POOLS work? (Uniswap, Curve, Balancer) - DEFI Explained](https://www.youtube.com/watch?v=cizLhxSKrAc)

    - [UNISWAP V3 - New Era Of AMMs? Architecture Explained](https://www.youtube.com/watch?v=Ehm-OYBmlPM)

    - Extra:

      - [An Overview of AMM Mechanisms by Matt Deible - Devcon Bogotá](https://www.youtube.com/watch?v=KxuyHfmLHP0)

      - [AAVE - The Road To $3 Billion - DEFI Explained](https://www.youtube.com/watch?v=WwE3lUq51gQ) (Lending protocol)

      - [https://yos.io/2018/11/10/bonding-curves/](https://yos.io/2018/11/10/bonding-curves/)

      - [https://medium.com/@buildwithbhavya/the-math-behind-pump-fun-b58fdb30ed77#:~:text=At%20its%20core%20lies%20a,skipping%20presales%20or%20team%20allocations](https://medium.com/@buildwithbhavya/the-math-behind-pump-fun-b58fdb30ed77#:~:text=At%20its%20core%20lies%20a,skipping%20presales%20or%20team%20allocations)

  - Practical Exercise

    - Using [Remix](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null) deploy [ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol). Mint tokens and use the methods balanceOf, approve, transferFrom etc.. to have as complete an understanding as possible.

    - Extra:

      - (Create a Liquidity Pool on Pancakeswap?)

      - (Interact with AAVE?)

---

- **Known Attacks**

  - Reentrancy (CEI Pattern)

  - Frontrunning (Commit-Reveal Scheme)

  - Extra:

    - Practice the following and previous ones with [https://ethernaut.openzeppelin.com/](https://ethernaut.openzeppelin.com/)

    - Understand these:

      - All storage variables can be accessed (independent of visibility)

      - Replay Attack

      - Reorder Attack

      - Delay Attack

      - Domain Change

      - Precision Loss

---

- **ERC vs EIP**

    - **EIP (Ethereum Improvement Proposal)**: A formal proposal document that describes standards, features, or changes to the Ethereum ecosystem. EIPs can cover protocol-level changes, application-level standards, or informational documentation. All standards start as EIPs.

      - [EIP Repository](https://github.com/ethereum/EIPs)

    - **ERC (Ethereum Request for Comments)**: A specific category of EIPs that focuses on application-level standards and conventions. ERCs are EIPs that have been accepted and standardized for smart contract interfaces and implementations. The term "ERC" is often used interchangeably with token standards, but it can also refer to other application-level standards.

    - **Summary**: EIP is the broader category (all proposals), while ERC is a subset of EIPs specifically for application-level standards. ERCs are numbered EIPs (e.g., ERC-20 is also EIP-20).

---

- **Useful standards**

  - **ERC-20 (Fungible Tokens)**

    - Standard for fungible tokens (each token is identical and interchangeable). Defines a common interface for tokens with functions like `transfer()`, `approve()`, `balanceOf()`, and `totalSupply()`. Used for cryptocurrencies, stablecoins, governance tokens, and any token where units are equivalent.

      - [EIP-20: ERC-20 Token Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md)

      - Projects that use this standard: Mostaza, Acme, Aura 

  - **ERC-721 (Non-Fungible Tokens - NFTs)**

    - Standard for non-fungible tokens where each token is unique and distinguishable. Each token has a unique identifier and can have its own metadata. Used for collectibles, digital art, gaming assets, and any unique digital item.

      - [EIP-721: ERC-721 Non-Fungible Token Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md)

      - Projects that use this standard: Acme (Through third web), 

  - **ERC-1155 (Multi-Token Standard)**

    - Unified standard that can represent both fungible and non-fungible tokens in a single contract. Supports batch operations (transfer multiple token types in one transaction). More gas-efficient for managing multiple token types. Used in gaming, where a contract might need to handle both currencies (fungible) and items (non-fungible).

      - [EIP-1155: ERC-1155 Multi Token Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1155.md)

  - **ERC-4626 (Tokenized Vault Standard)**

    - Standard for yield-bearing vaults that wrap ERC-20 tokens to generate yield. Provides a unified interface for vaults that accrue value over time through strategies like lending, staking, or liquidity provision. Enables composability between different yield-generating protocols and simplifies integration with DeFi applications. Used in yield aggregators, lending protocols, and automated yield strategies.

      - [EIP-4626: Tokenized Vault Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-4626.md)

  - **ERC-4337 (Account Abstraction)**

    - Standard for account abstraction without requiring consensus-layer changes. Allows smart contracts to act as wallets (smart contract wallets) with custom validation logic, sponsored transactions, signature aggregation, and recovery mechanisms. Enables gasless transactions, social recovery, and multi-sig wallets without protocol changes.

      - [EIP-4337: Account Abstraction using alt mempool](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-4337.md)

  - **EIP-712 (Structured Data Signing)**

    - Standard for signing typed, structured data instead of raw bytes. Provides a way to sign human-readable messages with type information, making signatures more secure and user-friendly. Used in meta-transactions, authentication systems, and any scenario where users need to sign structured data that can be verified on-chain. Enables wallets to display readable messages before signing.

      - [EIP-712: Typed structured data hashing and signing](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-712.md)

---

- **Additional interesting standards**

  - **ERC-6909 (Minimal Multi-Token Standard)**

    - A minimal, gas-efficient standard for contracts that manage multiple token types. Provides a simpler interface than ERC-1155, focusing on core functionality for token accounting and transfers. Designed for scenarios where multiple token types need to be tracked efficiently without the full feature set of ERC-1155. More gas-efficient for basic multi-token operations.

      - [EIP-6909: Minimal Multi-Token Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-6909.md)

  - **EIP-7702 (Set Code Authorization)**

    - Proposal that allows EOAs (Externally Owned Accounts) to temporarily execute code from a contract address during a transaction. Enables account abstraction features by allowing EOAs to behave like smart contracts for a single transaction without permanently converting them. Provides a way to use account abstraction without deploying a separate smart contract wallet. Allows users to enjoy the benefits of smart contract wallets (multi-sig, social recovery, etc.) while maintaining EOA addresses.

      - [EIP-7702: Set EOA Code](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-7702.md)

---

### Useful references:

[https://ethereum.org/en/developers/docs/intro-to-ethereum/](https://ethereum.org/en/developers/docs/intro-to-ethereum/)

[https://docs.soliditylang.org/en/v0.8.26/introduction-to-smart-contracts.html](https://docs.soliditylang.org/en/v0.8.26/introduction-to-smart-contracts.html)

[https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015](https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015)

[https://learnmeabitcoin.com](https://learnmeabitcoin.com)

[https://updraft.cyfrin.io/courses/blockchain-basics](https://updraft.cyfrin.io/courses/blockchain-basics)

[https://andersbrownworth.com/blockchain](https://andersbrownworth.com/blockchain)

[https://www.youtube.com/watch?v=GSIDS_lvRv4&pp=ygURY29tcHV0ZXJwaGlsZSBwa2M%3D](https://www.youtube.com/watch?v=GSIDS_lvRv4&pp=ygURY29tcHV0ZXJwaGlsZSBwa2M%3D)

---

### Old:

- Smart Contracts Solidity

- ABI ByteCode OPCodes
- Compilación de contrato (compresión)
- Almacenamiento en storage (variables dinámicas y no dinamicas)
- Variables immutables y constantes
- Emision de eventos & Log blooms.
- CREATE1 & CREATE2
