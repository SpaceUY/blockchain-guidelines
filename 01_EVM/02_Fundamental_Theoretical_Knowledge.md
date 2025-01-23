---
title: Fundamental Theoretical Knowledge
layout: home
parent: Ethereum Virtual Machine
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
