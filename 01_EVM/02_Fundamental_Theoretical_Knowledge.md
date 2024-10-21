---
title: Fundamental Theoretical Knowledge
layout: home
parent: Ethereum Virtual Machine
nav_order: 2
---


-   Criptografía

	-   Criptografía asimétrica: Propiedades (autenticidad, no repudio, no reusable)
    

		-   [Public Key Cryptography - Computerphile](https://www.youtube.com/watch?v=GSIDS_lvRv4)
    

	-   Curvas Elípticas: Operación Suma y Multiplicación, curva secp256k1
    

		-   [Elliptic Curve Diffie Hellman](https://www.youtube.com/watch?v=F3zzNa42-tQ)
    

			-   Curvas elipticas (0:00 - 9:00)
    
			-   Diffie Hellman (9:00 - 11:55) -> How to exchange a secret
    

		-   [Curvas Elipticas](https://docs.google.com/document/u/0/d/17RIfXlziCN3j5ST0eM0SsO5E-5Q2OJVqAn37TCy3A2s/edit)
    

	-   Criptografía asimétrica sobre curvas elípticas:
    

		-   [https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages](https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages)
    

			((r,s,v), Firma digital, Verificación de firma, Recuperación)

		-   [https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md)
    

	-   Problema de maleabilidad de las firmas:
    

		-   [https://www.youtube.com/shorts/RqOaaglSqlI](https://www.youtube.com/shorts/RqOaaglSqlI)
    

	-   Extra: Divertirse con [https://cryptohack.org/](https://cryptohack.org/)
    
	-   Ejercicios en 02_fundamentals/src/cryptography
    

  

- HD Wallets
    

	-   [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki), [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki), [BIP44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)
    

		-   [Blockchain tutorial 28: Bitcoin Improvement Proposal 39 (BIP-39) mnemonic words](https://www.youtube.com/watch?v=hRXcY_tIlrw)
    
		-   [Blockchain tutorial 29: Hierarchical Deterministic wallet - BIP32 and BIP44](https://www.youtube.com/watch?v=2HrMlVr1QX8)
    
		-   [https://tara-annison.medium.com/mnemonic-seed-phrases-bip39-6b843291834c](https://tara-annison.medium.com/mnemonic-seed-phrases-bip39-6b843291834c)
    
		-   Entender en términos generales la motivación de los estándares mencionados.
    
		-   Master private key and Master public key [https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/](https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/)

		-   Child Key derivation [https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/#child-key-derivation](https://learnmeabitcoin.com/technical/keys/hd-wallets/extended-keys/#child-key-derivation)
    

		-   Ejercicios en [02_fundamentals/src/hd-wallets](https://github.com/SpaceUY/blockchain-techbook/tree/main/src/02-fundamentals/hd-wallets)
    

  

-   EOA vs IOA
    

	-   [3_IntroducciÃ³n a Ethereum.pdf](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pág 15 a 20 [Autor David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))
    
	-   https://ethereum.org/en/developers/docs/accounts/
    
	-   [Ethereum Accounts Explained: Smart Contract vs Externally Owned Account (EOA)](https://www.youtube.com/watch?v=CbV3jrhj-Os&t=106s)
    
	-   [Ejercicio Práctico](https://colab.research.google.com/drive/1E8r0wHjeixSLifFXmoc0COP1-pjYSPcd#scrollTo=WSWBi6kVp7bc)
    

  

-   Blockchain
    

	-   Block, contenido, root de los arboles (state, transactions, receipts)
    

		-   [3_IntroducciÃ³n a Ethereum.pdf](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pág 32 a 40 [Autor David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))
    
		-   [https://ethereum.org/en/developers/docs/blocks/](https://ethereum.org/en/developers/docs/blocks/)
    
		-   [Simplified interactive view of a blockchain](https://andersbrownworth.com/blockchain/hash)
    

	-   Transactions
    

		-   [3_IntroducciÃ³n a Ethereum.pdf](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pág 27 a 31 [Autor David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit)) (Message Calls, Contract Creations)

		-   [https://ethereum.org/en/developers/docs/transactions/](https://ethereum.org/en/developers/docs/transactions/)
    

	-   Gas
    

		-   [3_IntroducciÃ³n a Ethereum.pdf](https://drive.google.com/open?id=1IdSVNGDu1ielZmN_2Tda5TaTUCNRhLoJ) (pág 22 a 27 [Autor David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit)) (Gas, GasLimit, Gas Price, OOG)

		-   [https://ethereum.org/en/developers/docs/gas/](https://ethereum.org/en/developers/docs/gas/)
    
		-   [Can ETH Become DEFLATIONARY? EIP 1559 Explained](https://www.youtube.com/watch?v=MGemhK9t44Q)
    

	-   [Blockchain Transactions Deep Dive: Análisis, Costos y más con Germán Küber](https://www.youtube.com/watch?v=FrCyT_FSdjQ)
    

		-   Ejecución de una transacción
    
		-   Costos de gas (distintos tipos de lecturas, escrituras)
    
		-   Refund de gas al limpiar valores en storage
    

  

-   JSON - RPC (Eth API)
    

	-   [https://ethereum.org/en/developers/docs/apis/json-rpc/](https://ethereum.org/en/developers/docs/apis/json-rpc/)
    
	-   [https://ethereum.github.io/execution-apis/api-documentation/](https://ethereum.github.io/execution-apis/api-documentation/)
    
	-   [https://stackoverflow.com/questions/50985798/difference-between-sendtransaction-and-sendrawtransaction-in-web3-py](https://stackoverflow.com/questions/50985798/difference-between-sendtransaction-and-sendrawtransaction-in-web3-py (Diferencia entre eth_sendTransaction y eth_sendRawTransaction)

	-   Ejercicio
    

		-   [Playground](https://ethereum-json-rpc.com/). Jugar con algunos de los siguientes:  
    eth_chainId, eth_blockNumber, eth_gasPrice, eth_maxPriorityFeePerGas, eth_getBalance, eth_getCode, eth_call, eth_estimateGas, eth_getBlockByNumber, eth_getBlockByHash, eth_getTransactionByHash, eth_getTransactionReceipt.
    

-   Blockchain almacenamiento
    

	-   [4_Almacenamiento en Ethereum.pdf](https://drive.google.com/open?id=1uJpX04AV36ffxKn-VWPJYhYe9U1lt34_) ([Autor David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))
    
	-   Extra: [Visualizacion Merkle Trees](https://blockchain-academy.hs-mittweida.de/merkle-tree/)
    
	-   Ejercicio Práctico
    

  

-   EVM (Ethereum Virtual Machine)
    

	-   [8_EVM - Ethereum Virtual Machine.pdf](https://drive.google.com/open?id=1dmQvvK8MGQdPwgtDX7SxExRcNnKa-ygU) ([Autor David Gimenez](https://docs.google.com/document/d/1lvfL4r0Awl2qXP5C1TbKo4cMk1fXxEL3vOIxWvZJt-w/edit))
    
	-   [EVM (Primera parte) | Taller Avanzado en Vivo con Germán Küber](https://www.youtube.com/watch?v=hT6IxwGr8hs) (Smart contract bytecode, opcods, EVM)

	-   Ejercicio Práctico
    

		-   Ver como es la ejecución de un código de solidity usando [https://www.evm.codes/playground](https://www.evm.codes/playground)
    

	-   Extra:  
    [https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015](https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015) (Es un poco viejo este articulo, pesado pero si a alguien le interesa complementar lo aprendido con esto que esta aquí, esta aun vigente)
    

  

-   Nodos y clientes
    

	-   [https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/](https://ethereum.org/en/developers/docs/nodes-and-clients/node-architecture/) (Ethereum consensus and execution client)

	-   [https://ethereum.org/en/developers/docs/nodes-and-clients/light-clients/](https://ethereum.org/en/developers/docs/nodes-and-clients/light-clients/) (Light nodes)

  

-   Algoritmos de consenso
    

	-   Problema de los generales bizantinos
    

		-   [Distributed Systems 2.2: The Byzantine generals problem](https://www.youtube.com/watch?v=LoGx_ldRBU0)
    
		-   Extra: [Two Generals' Problem Explained](https://www.youtube.com/watch?v=s8Wbt0b8bwY)

	-   [https://ethereum.org/en/developers/docs/consensus-mechanisms/](https://ethereum.org/en/developers/docs/consensus-mechanisms/)
    

		-   [Understanding Blockchain Consensus Mechanisms](https://www.youtube.com/watch?v=ojxfbN78WFQ)
    

	-   PoW
    

		-   [https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/)
    

			-   [What is Proof of Work (PoW)｜Explained For Beginners](https://www.youtube.com/watch?v=3EUAcxhuoU4)
    

	-   PoS
    

		-   [QUE ES EL STAKING Y PROOF OF STAKE??! EXPLICACION BASICA!!](https://www.youtube.com/watch?v=bQYExyRc14M) (No es el mejor video, las mejores explicaciones, PERO el contenido es el el apropiado)

	-   PoS en Ethereum
    

		-   [Future-block MEV in Proof of Stake by Torgin Mackinga | Devcon Bogotá](https://www.youtube.com/watch?v=rnR7puADz-o)
    
		-   [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos)
    

			-   [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#transaction-execution-ethereum-pos](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/#transaction-execution-ethereum-pos)
    
			-   [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/block-proposal/](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/block-proposal/)
    
			-   [https://ethereum.org/en/developers/docs/networking-layer/#connecting-clients](https://ethereum.org/en/developers/docs/networking-layer/#connecting-clients)
    

  

		-   Extra:
    

			-   [Updates on Proposer-Builder Separation by Barnabé Monnot | Devcon Bogotá](https://www.youtube.com/watch?v=sQQ2UYB3qOI)
    
			-   [¡Hack de $25.000.000 USD MEV Boost Explicado en Vivo!](https://www.youtube.com/watch?v=Mlj2PFTDSGI) (Ataque MEV pero que repasa todos los conceptos de cómo se arman los bloques, searchers, etc)

	-   PoA
    

		-   [https://ethereum.org/en/developers/docs/consensus-mechanisms/poa/](https://ethereum.org/en/developers/docs/consensus-mechanisms/poa/)
    

  

-   Meta txs
    

	-   Forwarder, EIP712, ERC2771 (Context y Forwarder)
    
	-   Reply attack protection (Nonce nativo vs “Nonce artificial”)
    

  
  

-   Patrones de Upgradeability

	-   Conceptualmente y sus beneficios: Transparent, UUPs, Beacon, Diamond, [Proxies, Beacons & Diamond Pattern - EVM Expeditions #02 - byterocket](https://www.youtube.com/watch?v=iXLoSVcVhUg)

	-   Ejercicio Práctico:

		-   (Mirando eth scan, ir a un contrato upgradeable, identificar cual es la implementación, cual es el proxy, como invocar un read, write..)
    

  

-   Dominio especifico (NFTs)
    

	-   NFTs ([ERC721](https://docs.openzeppelin.com/contracts/2.x/api/token/erc721), [ERC1155](https://docs.openzeppelin.com/contracts/3.x/erc1155)).
    
	-   NFT metadata standard
    

		-   [What is IPFS and How Does it Work?](https://www.youtube.com/watch?v=z2judsbo-5E)
    
		-   [https://docs.opensea.io/docs/metadata-standards](https://docs.opensea.io/docs/metadata-standards)
    

	-   Ejercicio Práctico
    

		-   Usando [Remix](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null) deployar [ERC721](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol) y [ERC1155](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC1155/ERC1155.sol). La metadata puede subirse a IPFS mirando el siguiente video  [05. Upload your art and metadata to IPFS with Pinata.cloud](https://www.youtube.com/watch?v=mSUpcZA5o0). Mintear NFTs y utilizar los metodos balanceOf, approve, transferFrom etc.. para tener un entendimiento lo más completo posible.

  

-   Dominio especifico (DeFI)
    

	-   [ERC20](https://docs.openzeppelin.com/contracts/2.x/api/token/erc20)
    
	-   Liquidity Pool & AMM
    

		-   [What is an Automated Market Maker? (Liquidity Pool Algorithm)](https://www.youtube.com/watch?v=1PbZMudPP5E)
    
		-   [How do LIQUIDITY POOLS work? (Uniswap, Curve, Balancer) | DEFI Explained](https://www.youtube.com/watch?v=cizLhxSKrAc)
    
		-   [UNISWAP V3 - New Era Of AMMs? Architecture Explained](https://www.youtube.com/watch?v=Ehm-OYBmlPM)
    
		-   Extra:
    

			-   [An Overview of AMM Mechanisms by Matt Deible | Devcon Bogotá](https://www.youtube.com/watch?v=KxuyHfmLHP0)
    
			-   [AAVE - The Road To $3 Billion - DEFI Explained](https://www.youtube.com/watch?v=WwE3lUq51gQ) (Lending protocol)
    
			-   [https://yos.io/2018/11/10/bonding-curves/](https://yos.io/2018/11/10/bonding-curves/)
    
			-   [https://medium.com/@buildwithbhavya/the-math-behind-pump-fun-b58fdb30ed77#:~:text=At%20its%20core%20lies%20a,skipping%20presales%20or%20team%20allocations](https://medium.com/@buildwithbhavya/the-math-behind-pump-fun-b58fdb30ed77#:~:text=At%20its%20core%20lies%20a,skipping%20presales%20or%20team%20allocations)
    

	-   Ejercicio Práctico
    

		-   Usando [Remix](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null) deployar [ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol). Mintear tokens, utilizar los metodos balanceOf, approve, transferFrom etc.. para tener un entendimiento lo más completo posible.

		-   Extra:
    

			-   (Crear un pool de liquidez en panckakeswap?)
    
			-   (Interactuar con AAVE)
   

-   Ataques conocidos
    

	-   Reentrancy (CEI Pattern)
    
	-   Frontrunning (Commit-Reveal Scheme)
    
	-   Extra:
    

		-   Ejercitar los siguientes y anteriores con [https://ethernaut.openzeppelin.com/](https://ethernaut.openzeppelin.com/)
    
		-   Entender estos otros:
    

			-   All storage variables can be accessed (independent of visibility)
    
			-   Replay Attack
    
			-   Reorder Attack
    
			-   Delay Attack
    
			-   Domain Change
    
			-   Precision Loss
    

### Referencias de utilidad:  
  

[https://ethereum.org/en/developers/docs/intro-to-ethereum/](https://ethereum.org/en/developers/docs/intro-to-ethereum/)

[https://docs.soliditylang.org/en/v0.8.26/introduction-to-smart-contracts.html](https://docs.soliditylang.org/en/v0.8.26/introduction-to-smart-contracts.html)

[https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015](https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015)

[https://learnmeabitcoin.com](https://learnmeabitcoin.com)

[https://updraft.cyfrin.io/courses/blockchain-basics](https://updraft.cyfrin.io/courses/blockchain-basics)

[https://andersbrownworth.com/blockchain](https://andersbrownworth.com/blockchain)

[https://www.youtube.com/watch?v=GSIDS_lvRv4&pp=ygURY29tcHV0ZXJwaGlsZSBwa2M%3D](https://www.youtube.com/watch?v=GSIDS_lvRv4&pp=ygURY29tcHV0ZXJwaGlsZSBwa2M%3D)

  
  

### Old:  

-   Smart Contracts Solidity

-   ABI ByteCode OPCodes
    
-   Compilación de contrato (compresión)
    
-   Almacenamiento en storage (variables dinámicas y no dinamicas)
    
-   Variables immutables y constantes
    
-   Emision de eventos & Log blooms.
    
-   CREATE1 & CREATE2