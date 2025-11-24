---
title: Blockchain Projects
layout: home
nav_order: 5
---

## Proyectos

| Project                       | Blockchains          | Devs                               | Updated At            |
| ----------------------------- | -------------------- | ---------------------------------- | --------------------- |
| [Collector Crypt](#coll-crypt)| [Solana](compendium#solana) | Tomi Freire | |
| [Division One Crypto](#d1c)   | [Solana](compendium#solana) | Tomi Freire | |
| [ApeBond](#ape-bond)          | [Solana](compendium#solana) | Diego García, Tomi Freire | |
| [Mostaza](#mostaza)           | EVM | Tomi Freire | |
| [Fight FI](#fight-fi)         | Flow, [Aptos](compendium#aptos) | Diego García, Santi Grangetto | |
| [Rarible](#rarible)           | EVM, [Solana](compendium#solana) | Gonza Bustos | |
| [Duel](#duel)                 | Evm-Base | Tomi Freire, Gonza Bustos, Facu Panizza | 21/05/2025 |
| [Safe Fun](#safe-fun)         | [Solana](compendium#solana) | Rocko Pintos, Santi Grangetto, Tomi Freire | Sep. 2024 - Oct. 2024 |
| [Penumbra](#penumbra)         | Cosmos-like | Alexis Wolfsdorf | 21/05/2025 |
| [CryptoArt](#cryptoart)       | EVM | Jona Allegretti | |
| [Blockus](#blockus)           | EVM, [Sui](compendium#sui) | Alexis Wolfsdorf, Rocko Pintos | |
| [Acme](#acme)                 | EVM, [Solana](compendium#solana) | Diego García, Rocko Pintos | |
| [W3E](#w3e)                   | EVM | Gonza Othacehe | |
| [Phenom Poker](#phenom-poker) | EVM | Juanma Pereira, Agus Chiarotto | |
| [Blockbound](#blockbound)     | EVM, [Solana](compendium#solana), Bitcoin | Elina García, Juanma Pereira | |
| [Lancelot](#lancelot)         | EVM, [Solana](compendium#solana) | Facu Panizza | |

---

# Penumbra

### Updated at: [21/05/2025]

**Descripción**
Blockchain del ecosistema Cosmos que busca hacer un enhance en la privacidad al interactuar con servicios comunes de DeFi (Staking, Swaping, DEX). Esto se logra agregando capas de abstraccion de view/write keys, public commitments y private notes en conjunto con ZKproofs.

## TokenFactory en Penumbra Core

### Updated at: [21/05/2025]

**Descripción**

Es donde la magia ocurre, componentes para cada servicio (DEX, LP, Auctions, etc) en una app desde 0 en Rust usando Protobuf para comunicacion con servicios externos y cnidarium.
Se inició el desarrollo del token factory, siguiendo el [blog](https://forum.penumbra.zone/t/token-factory-on-penumbra/127).

**Links**

https://protocol.penumbra.zone/main/penumbra.html
https://guide.penumbra.zone/
https://github.com/penumbra-zone/penumbra o https://github.com/AWolfsdorf/penumbra/tree/space/awolfsdorf/token_factory

**Tech Stack**  
Rust

**Chains**  
Penumbra (Cosmos Ecosystem)

**Repositorio**  
Github, see links

**Devs**  
Alexis Wolfsdorf, Tomas Freire

**Desafíos técnicos**

- Comprensión del funcionamiento general del protocolo. HARD
- Entendimiento de Zk proofs y su uso en sistemas de privacidad.

## Tokenomics Dashboard

### Updated at: [21/05/2025]

**Descripción**

Dashboard donde se busca mostrar la importancia y comportamiento de un token en especifico, en este caso UM$. Se muestran graficos de movimiento de precio, inflacion, market cap, etc; para mostrar transparencia ante los posibles cliente/usuarios.

**Tech Stack**  
Nextjs

**Chains**  
Penumbra (Cosmos Ecosystem)

**Repositorio**  
https://bitbucket.org/spaceuy/tokenomics-dashboard/src/main/

**Devs**  
Alexis Wolfsdorf

**Desafíos técnicos**

- Uso de chaching optimizado por estar accediendo directamente desde nextjs a una base de datos del cliente.
- Uso de librerias de charts ([Apache Echarts](https://echarts.apache.org/))

## ApeBond

**Descripción**

ApeBond es un protocolo DeFi en el que otros protocolos (partners) y DAOs pueden vender sus tokens (Bonds) con un descuento a usuarios para obtener liquidez instantánea en lugar de hacerlo por medios más tradicionales.

**Tech Stack**  
Solana, Anchor, Rust, React

**Chains**  
Solana

**Devs**  
Diego García, Tomi Freire

**Desafíos técnicos**

- Migración del protocolo ya establecido en cadenas EVM a Solana
- Implementación de nuevos features en Solana

## Mostaza

### Updated at: [21/05/2025]

**Descripción**  
Fintech colombiana para servicios financieros Web3. MVP con:

- Billetera USDT fondeable por transferencia o tarjeta
- Conversión COP ↔ USDT
- Tarjeta virtual
- Inversión en USDM (4–5% APY)
- Panel de administración

**Tech Stack**  
NextJS, NestJS, React Native, MongoDB, Solidity

**Chains**  
Polygon

**Repositorio**  
Bitbucket (Space)

**Devs**  
Pablo Castaño, Carlos Garcia, Santiago Grangetto, Samuel Sosa, Florencia Pereira, Tomas Freire

**Desafíos técnicos**

- Integración real-time entre tarjeta, backend, Binance y contratos
- Conversión real-time entre COP y USDT con mecanismo de fijación de cambio

## Fight FI

## Duel

### Updated at: [21/5/2025]

**Descripción**  
Aplicación de apuestas entre dos participantes usando smart contracts

**Tech Stack**  
Solidity, Foundry, Nextjs

**Chains**
Base

**Repositorio**
Github (En Garde Labs)

**Devs**
Tomás Freire

**Desafíos técnicos**

- Realizar la dinámica de apuestas de la manera más eficiente posible en términos de gas y simpleza para el usuario sin resignar funcionalidades.

## Rarible

**Devs**
Gonza

---

## Safe Fun

### Updated at: [21/05/2025]

**Descripción**  
Design/develop a Solana program with Rust using Anchor

Using Rust macros and polymorphism to enhance code reuse

The program supports:

- The creation of tokens along with their corresponding presales
- Staged, Bonding Curve and Fair Bonding Curve presale types supported
- Automate Market Maker (AMM) & Liquidity pool creation using OpenBook-Dex & Raydium programs
- Forked Raydium Contract Instructions https://github.com/RoSpaceDev/raydium-contract-instructions from https://github.com/raydium-io/raydium-contract-instructions, to use amm-anchor with latest dependencies.

Everything was designed in a way it does not require central entities to trigger the market and liquidity pool creation.

**Tech Stack**  
Rust, Anchor, TypeScript, Metaplex

**Chains**  
Solana

**Repositorio**  
Github (Space) https://github.com/SpaceUY/safe-fun - https://github.com/RoSpaceDev/raydium-contract-instructions

**Devs**  
Rocko, Santi Grangetto, Tomi

**Desafíos técnicos**

- Polimorfismo en rust
- Uso de macros en rust
- Algoritmos de bonding curve
- Uso de Raydium y OpenBook-Dex
- Pago de fees, se usó WSOL en vez de sol

---

## Cryptoart

### Updated at: [28/08/2024]

**Descripción**  
Galería de NFTs con minteo, trading y burning. Los holders pueden adquirir arte físico vía Shopify. Contrato upgradeable, tokens ERC-721.

**Tech Stack**  
ReactTS Vite, NestJS, Postgres, Shopify app-blocks, Solidity

**Chains**  
Base

**Repositorio**  
Bitbucket (Space)

**Devs**  
Jona, Facu

**Desafíos técnicos**

- Tracking de eventos en tiempo real (Alchemy)
- Multi-metadata con updates y eventos
- Minteo con firma centralizada ("vouchers")
- User Stories en chain logs

---

## Blockus

### Updated at: [28/08/2024]

**Descripción**  
Proyecto dentro de la industria del Web3 gaming. Plataforma que busca facilitar la integración de tecnología web3 a creadores de videojuegos. Ofrece API y Backoffice.

**Tech stack**  
React, Node con Express, Firebase

**Devs**  
Rocko, Alexis

**Desafíos técnicos**

- Multichain (Múltiples EVMs)
- Solución de billeteras custodia (clave privada en BD, cross-mint con MPC)
- Paymaster con Gelato
- Uso de Reservoir para marketplace
- Create2 para creación de contratos
- ERC1155 factory con Beacon Pattern
- Minteo a través de autoridad centralizada en backend que firma "vouchers"
- Algoritmo para hacer derivacions deterministicas sobre una master key basados en un timestamp

**Presentación en meet up**  
Link a canvas

---

## Acme

### Updated at: [28/08/2024]

**Descripción**  
Plataforma que permite transaccionar de forma sencilla e intuitiva. Los usuarios completan distintos "intents" como:

- Pagos cripto (con on ramp si es necesario)
- Comprar/Vender tokens
- Claimear NFTs
- Deploy de contratos de NFTs y tokens fungibles
- Registro y ejecución de contratos custom

Desarrolladores pueden crear intents usando una API documentada.

**Tech Stack**  
React, Node con Wundergraph, Prisma, Postgres, Docker

**Devs**  
Rocko, Gonza, Diego Garcia, Andre Neyra

**Desafíos técnicos**

- MM (Match Maker): ruta óptima para ejecución
- OMS (Order Management System)
- Multichain (EVM y Solana)
- Smart Wallets (Safe + Gelato relay kit sdk)
- Solana durable nonces
- Dex aggregator (Lifi, Jupiter)
- OnRamp integration (Transak, Mudrex)

---

## W3E

**Devs**  
Gonza O

---

## Phenom Poker

**Descripción**  
Aplicación web para jugar al póker online con apuestas en USDT. Cuenta con licencia legal y cumple con regulación KYC. Incluye:

- Replays de manos, chat, notas, amigos
- +700 variantes de póker
- Personalización del avatar y mesa
- Smart contract de distribución de utilidades
- Revenue sharing con jugadores
- Backoffice para administración y métricas

**Tech Stack**  
ReactTS, Tailwind, Redux, NestJS, Postgres, Docker, Kubernetes, Privy, Datadog, Agones, CSI-Secrets-Store, Contour

**Repositorio**  
[GitLab del cliente](https://gitlab.com/)

**Devs**  
Agustín Chiarotto, David Cervi, Elina Garcia, Juan Manuel Pereira, Carlos Garcia

**Desafíos técnicos**

- UI compleja de la mesa de póker (componentes, animaciones, sonidos, websockets, chat, replays)
- Ruteo HTTPS a gameservers
- Open Telemetry y Grafana para métricas
- Diseño stateless para escalabilidad

---

## Blockbound

**Descripción**  
Plataforma de contabilidad para cripto y fiat, útil para declaraciones fiscales en EE.UU. Trackea ingresos y egresos entre múltiples chains y bancos.

**Tech Stack**  
React, Node, NestJS, Serverless Framework, AWS Lambda, Step Functions

**Devs**  
Eli, Juanma

**APIs utilizadas**

- Ethereum: Etherscan API
- Solana: Solscan API
- Bitcoin y otros: Blockchair
- Exchanges: ccxt

**Desafíos técnicos**

- Ingesta y procesamiento de millones de transacciones
- Unificación de formatos de datos
- Manejo de datos incompletos o inconsistentes
- Procesos de ingestión de largo plazo sin congestionar backend

---

## Lancelot

**Devs**  
Facu Panizza

---
