---
title: Smart Contract Dev With Solidity
layout: home
parent: Ethereum Virtual Machine
nav_order: 3
---

# Smart Contract Dev With Solidity

---

Video: [Delving into EVM: How Ethereum Works Backstage](https://hackernoon.com/es/profundizando-en-evm-como-ethereum-works-backstage-ac7efa1f0015)

Build step by step based on: [https://docs.google.com/document/d/1eRGYyEaO0O83Yx9EhJF1Fl-5-J0Dhn3ZNEbDNnyj5Xw/edit?usp=sharing  
](https://docs.google.com/document/d/1eRGYyEaO0O83Yx9EhJF1Fl-5-J0Dhn3ZNEbDNnyj5Xw/edit?usp=sharing)

**_Pending:_**

- Storage Layout
- Upgradeability
- Meta Transactions

### Upgradeability:

- Implementación custom, siguiendo el curso de cyfrin de solidity

- Ver este video de OZ: [https://www.youtube.com/watch?v=kWUDTZhxKZI](https://www.youtube.com/watch?v=kWUDTZhxKZI)

### Testing:

- Static (Slither)

- Fuzzing (Echidna is better, but there’s an integrated fuzzer within foundry)

- Symbolic Execution ([Mythril](https://joran-honig.medium.com/introduction-to-mythril-classic-and-symbolic-execution-ef59339f259b))

[https://github.com/trailofbits/eth-security-toolbox](https://github.com/trailofbits/eth-security-toolbox)

## Style Guide

Space dev has developed it's [own style guide](/peladito-rules/blockchain_rules.md), extracting information from different sources, please follow them along to maintain consistency with all teams.

For more information please check the following links:

- [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html) - Official Solidity documentation style guide
- [Chainlink Style Guide](https://github.com/smartcontractkit/chainlink-evm/blob/develop/contracts/STYLE_GUIDE.md) - Chainlink's Solidity style guide
- [OpenZeppelin Contracts](https://github.com/OpenZeppelin/openzeppelin-contracts) - Standard secure smart contract implementations
- [Ethereum Smart Contract Best Practices](https://consensys.github.io/smart-contract-best-practices/) - Comprehensive security guidelines
- [Foundry Documentation](https://book.getfoundry.sh/) - Foundry development framework documentation
- [NatSpec Format](https://docs.soliditylang.org/en/latest/natspec-format.html) - Ethereum Natural Specification Format documentation
