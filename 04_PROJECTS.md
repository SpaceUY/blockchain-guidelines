---
title: Blockchain Projects
layout: blockchain projects
nav_order: 4
---

## Proyectos

- Blockus
- Acme
- W3E
- Blockbound
- Rarible
- Phenom Poker
- Cryptoart
- Lancelot
- Mostaza

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
- Minteo a través de autoridad centralizada en backend que firma “vouchers”

**Presentación en meet up**  
Link a canvas

---

## Acme

### Updated at: [28/08/2024]

**Descripción**  
Plataforma que permite transaccionar de forma sencilla e intuitiva. Los usuarios completan distintos “intents” como:

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
Gonza

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

## Rarible

**Devs**  
Gonza

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
- Minteo con firma centralizada (“vouchers”)
- User Stories en chain logs

---

## Lancelot

**Devs**  
Facu Panizza

---

## Mostaza

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
