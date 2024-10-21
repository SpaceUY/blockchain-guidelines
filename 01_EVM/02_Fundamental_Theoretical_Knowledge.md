---
title: Fundamental Theoretical Knowledge
layout: home
parent: Ethereum Virtual Machine
nav_order: 2
---

Criptografía
Criptografía asimétrica: Propiedades (autenticidad, no repudio, no reusable)
Public Key Cryptography - Computerphile	
Curvas Elípticas: Operación Suma y Multiplicación, curva secp256k1
Elliptic Curve Diffie Hellman
Curvas elipticas (0:00 - 9:00)
Diffie Hellman (9:00 - 11:55) -> How to exchange a secret 
Curvas Elipticas
Criptografía asimétrica sobre curvas elípticas: 
https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages
((r,s,v), Firma digital, Verificación de firma, Recuperación)
https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md
Problema de maleabilidad de las firmas:
https://www.youtube.com/shorts/RqOaaglSqlI
Extra: Divertirse con https://cryptohack.org/
Ejercicios en 02_fundamentals/src/cryptography

HDWallets
BIP39, BIP32, BIP44
Blockchain tutorial 28: Bitcoin Improvement Proposal 39 (BIP-39) mnemonic words
Blockchain tutorial 29: Hierarchical Deterministic wallet - BIP32 and BIP44
https://tara-annison.medium.com/mnemonic-seed-phrases-bip39-6b843291834c
Entender en términos generales la motivación de los estándares mencionados.
Master private key and Master public key
https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/
Child Key derivation https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/#child-key-derivation
Ejercicios en 02_fundamentals/src/hd-wallets

EOA vs IOA
3_IntroducciÃ³n a Ethereum.pdf (pág 15 a 20 Autor David Gimenez)
https://ethereum.org/en/developers/docs/accounts/
Ethereum Accounts Explained: Smart Contract vs Externally Owned Account (EOA)
Ejercicio Práctico

Blockchain
Block, contenido, root de los arboles (state, transactions, receipts)
3_IntroducciÃ³n a Ethereum.pdf (pág 32 a 40 Autor David Gimenez)
https://ethereum.org/en/developers/docs/blocks/
Simplified interactive view of a blockchain
Transactions
3_IntroducciÃ³n a Ethereum.pdf (pág 27 a 31 Autor David Gimenez)
(Message Calls, Contract Creations)
https://ethereum.org/en/developers/docs/transactions/ 
Gas
3_IntroducciÃ³n a Ethereum.pdf (pág 22 a 27 Autor David Gimenez)
(Gas, GasLimit, Gas Price, OOG)
https://ethereum.org/en/developers/docs/gas/ 
Can ETH Become DEFLATIONARY? EIP 1559 Explained
Blockchain Transactions Deep Dive: Análisis, Costos y más con Germán Küber
Ejecución de una transacción
Costos de gas (distintos tipos de lecturas, escrituras)
Refund de gas al limpiar valores en storage

JSON - RPC (Eth API)
https://ethereum.org/en/developers/docs/apis/json-rpc/
https://ethereum.github.io/execution-apis/api-documentation/
https://stackoverflow.com/questions/50985798/difference-between-sendtransaction-and-sendrawtransaction-in-web3-py
(Diferencia entre eth_sendTransaction y eth_sendRawTransaction)
Ejercicio
Playground. Jugar con algunos de los siguientes:
eth_chainId, eth_blockNumber, eth_gasPrice, eth_maxPriorityFeePerGas, eth_getBalance, eth_getCode, eth_call, eth_estimateGas, eth_getBlockByNumber, eth_getBlockByHash, eth_getTransactionByHash, eth_getTransactionReceipt.
	
Blockchain almacenamiento 
4_Almacenamiento en Ethereum.pdf (Autor David Gimenez)
Extra: Visualizacion Merkle Trees
Ejercicio Práctico

EVM (Ethereum Virtual Machine)
8_EVM - Ethereum Virtual Machine.pdf (Autor David Gimenez)
EVM (Primera parte) | Taller Avanzado en Vivo con Germán Küber
(Smart contract bytecode, opcods, EVM)
Ejercicio Práctico
Ver como es la ejecución de un código de solidity usando  https://www.evm.codes/playground
Extra:
https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015 (Es un poco viejo este articulo, pesado pero si a alguien le interesa complementar lo aprendido con esto que esta aquí, esta aun vigente)

Nodos y clientes
https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/
(Ethereum consensus and execution client)
https://ethereum.org/en/developers/docs/nodes-and-clients/light-clients/
		(Light nodes)

Algoritmos de consenso
Problema de los generales bizantinos
Distributed Systems 2.2: The Byzantine generals problem	
Extra:
Two Generals' Problem Explained
https://ethereum.org/en/developers/docs/consensus-mechanisms/
Understanding Blockchain Consensus Mechanisms
PoW
https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/
What is Proof of Work (PoW)｜Explained For Beginners
PoS 
QUE ES EL STAKING Y PROOF OF STAKE??! EXPLICACION BASICA!!
(No es el mejor video, las mejores explicaciones, PERO el contenido es el el apropiado)
PoS en Ethereum
Future-block MEV in Proof of Stake by Torgin Mackinga | Devcon Bogotá
https://ethereum.org/en/developers/docs/consensus-mechanisms/pos
https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#transaction-execution-ethereum-pos
https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/block-proposal/
https://ethereum.org/en/developers/docs/networking-layer/#connecting-clients 

Extra: 
Updates on Proposer-Builder Separation by Barnabé Monnot | Devcon Bogotá
¡Hack de $25.000.000 USD MEV Boost Explicado en Vivo!	
(Ataque MEV pero que repasa todos los conceptos de cómo se arman los bloques, searchers, etc)
PoA
 https://ethereum.org/en/developers/docs/consensus-mechanisms/poa/

Meta txs
Forwarder, EIP712, ERC2771 (Context y Forwarder)
Reply attack protection (Nonce nativo vs “Nonce artificial”)


Patrones de Upgradeability
Conceptualmente y sus beneficios: Transparent, UUPs, Beacon, Diamond
Proxies, Beacons & Diamond Pattern - EVM Expeditions #02 - byterocket
Ejercicio Práctico:
(Mirando eth scan, ir a un contrato upgradeable, identificar cual es la implementación, cual es el proxy, como invocar un read, write..)  

Dominio especifico (NFTs)
NFTs (ERC721, ERC1155).
NFT metadata standard
What is IPFS and How Does it Work?
https://docs.opensea.io/docs/metadata-standards
Ejercicio Práctico
Usando Remix deployar ERC721 y ERC1155. 
La metadata puede subirse a IPFS mirando el siguiente video 05. Upload your art and metadata to IPFS with Pinata.cloud
Mintear NFTs y utilizar los metodos balanceOf, approve, transferFrom etc.. para tener un entendimiento lo más completo posible.

Dominio especifico (DeFI)
ERC20
Liquidity Pool & AMM
What is an Automated Market Maker? (Liquidity Pool Algorithm)
How do LIQUIDITY POOLS work? (Uniswap, Curve, Balancer) | DEFI Explained
UNISWAP V3 - New Era Of AMMs? Architecture Explained
Extra:
An Overview of AMM Mechanisms by Matt Deible | Devcon Bogotá
AAVE - The Road To $3 Billion - DEFI Explained (Lending protocol)
https://yos.io/2018/11/10/bonding-curves/
https://medium.com/@buildwithbhavya/the-math-behind-pump-fun-b58fdb30ed77#:~:text=At%20its%20core%20lies%20a,skipping%20presales%20or%20team%20allocations
Ejercicio Práctico
Usando Remix deployar ERC20
Mintear tokens, utilizar los metodos balanceOf, approve, transferFrom etc.. para tener un entendimiento lo más completo posible.
Extra:
(Crear un pool de liquidez en panckakeswap?)
(Interactuar con AAVE)


 Ataques conocidos
Reentrancy (CEI Pattern)
Frontrunning (Commit-Reveal Scheme)
Extra:
Ejercitar los siguientes y anteriores con https://ethernaut.openzeppelin.com/
Entender estos otros:
All storage variables can be accessed (independent of visibility)
Replay Attack
Reorder Attack
Delay Attack
Domain Change
Precision Loss
