---
title: Advanced Topics
layout: home
parent: Solana Blockchain Platform
nav_oder: 3
---

# Advanced Topics
---

## Solana Frequently Asked Questions (FAQ) Guide

1.  I may be misunderstanding something, but can a PDA be used as a signer? E.g., in the cases of nested calls?  
    RE: PDA doesn't have a private key so it can't sign
    
2.  Pyth is push based oracle?  
    RE: Pyth was initially designed as a push-based oracle on Solana, where price updates were pushed to the blockchain at regular intervals. However, due to certain limitations, including inefficiencies during periods of network congestion, Pyth has transitioned to a pull-based oracle system. They can be used as a source of authority or to authorize certain actions, but the actual signing must be done by a valid signer (an account with a private key).
    
3.  How does the mempool work in solana?  
    RE: there is no mempool in solana. That transactions flow directly to the node that will propose the block (the leader).
    
4.  What is "Durable Nonce" in solana  
    RE:
    
5.  Are Actions part of Solana Pay or do I choose one or the other?  
    RE: they are a part of Solana Pay
    
6.  Durable nonces - I guess its not a actually replay attack but it said the "Attacker can trick user into signing a safe transaction and maliciously update it later  
    RE: you can't change data of a signed transaction  
    RERE: sorry "it" refers to contract, != tx. re No 3. > https://medium.com/@pandaly520/how-to-avoid-solana-scams-8d2b7b62359f > only code check can prevent?
    
7.  Can fees be accurately pre-computed for transactions?  
    RE: yes, fees are constant on Solana for now ( of course unless you want to pay a priority fee or MEV tip). here's a link for further reading: [https://www.helius.dev/blog/priority-fees-understanding-solanas-transaction-fee-mechanics](https://www.helius.dev/blog/priority-fees-understanding-solanas-transaction-fee-mechanics)
    
8.  At a guess, would dev. costs be more than double to develop Actions code in Rust instead of using J.S. libs.?  
    RE: Yes, Rust development is likely to cost more than double compared to using JavaScript due to its complexity and longer development time.
    
9.  What is the max size of a block in solana? What is the unit to measure it size? In bictoin it is weight in bytes, in ethereum is the gas, in solana?  
    RE: 48 million compute units. There might be also a limit of 128MB. Not 100% sure. I assume the block size is what comes first: 48 mill CU or 128MB  
    further reading here: [https://solana.com/uk/docs/core/fees#compute-unit-limit](https://solana.com/uk/docs/core/fees#compute-unit-limit)
    
10.  In solidity, you need to use proxy patterns to upgrade contracts. I know in solana it works different. How adding instructions to an existant program is done?  
    RE: Just upgrade the program with new version. It is much simpler as programs are stateless.
    
11.  What are the main design patterns when developing programs in Solana?  
    RE: The main design patterns in Solana include Cross-Program Invocation (CPI), Program Derived Addresses (PDA), Token and Associated Token Accounts, and Accounts/Data Storage management.
    
12.  Regarding upgradeability. Ok so, every program in solana can be modified? Can I break this "upgradeability" in some way if I want the program to be immutable?  
    RE: remove the upgrade authority during deployment, ensuring it can’t be modified later.