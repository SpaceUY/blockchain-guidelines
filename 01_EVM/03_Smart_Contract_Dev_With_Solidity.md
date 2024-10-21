---
title: Smart Contract Dev With Solidity
layout: home
parent: Ethereum Virtual Machine
nav_order: 3
---

https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015

Construir punto a punto basado en:
https://docs.google.com/document/d/1eRGYyEaO0O83Yx9EhJF1Fl-5-J0Dhn3ZNEbDNnyj5Xw/edit?usp=sharing
(Falta el almacenamiento de variables)
(Considerar tmb upgradability)
(Meta txs)


Upgradeability:


-Implementación custom, siguiendo el curso de cyfrin de solidity
-Ver este video de OZ: https://www.youtube.com/watch?v=kWUDTZhxKZI

Testing:
- Static (Slither)
- Fuzzing (Echidna is better, but there’s an integrated fuzzer within foundry)
- Symbolic Exec (Mythril)
https://github.com/trailofbits/eth-security-toolbox 
