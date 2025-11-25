---
title: Real World Assets (RWAs)
layout: home
parent: Miscellaneous
---

# Real World Assets
---

### ERC 725 - Ethereum Identity Standard

-   Purpose: A standard for creating and managing a digital identity on the Ethereum blockchain.
    
-   Features: Defines a smart contract that can represent an identity, allowing the management of keys and claims (such as attestations from third parties). It supports the creation of decentralized identities that can interact with other smart contracts and services.
    
-   Status: This standard is still in the proposal stage but is recognized as a foundation for decentralized identity systems.
    

This standard is often paired with ERC 735, which handles claims associated with these identities.

---

### ERC 734 - Key Manager Standard

**Purpose**

-   ERC 734 defines a standard for managing keys within an identity contract, such as those defined by ERC 725. It allows for the addition, removal, and management of keys associated with an identity in a secure and standardized manner.
    

**Key Features**

1.  Key Management:
    

-   The standard specifies functions for adding, removing, and managing keys. Each key can be assigned specific roles or purposes, such as signing transactions, interacting with contracts, or managing permissions.
    

2.  Roles and Purposes:
    

-   Keys can have different roles or purposes, such as:
    

-   Purpose 1: Managing the identity itself (e.g., owner keys).
    
-   Purpose 2: Executing actions on behalf of the identity (e.g., delegate keys).
    
-   Purpose 3: Claim management (e.g., keys that interact with ERC 735 claims).
    

3.  Permissions:
    

-   ERC 734 allows for granular control over which keys have what permissions, enhancing the security and flexibility of identity contracts.

---  

### ERC 735 - Claim Holder Standard

-   Purpose: Works in conjunction with ERC 725 to manage claims (attestations or credentials) about an identity.
    
-   Features: Allows identities to hold claims issued by others, making it a core component of decentralized identity systems. Claims can be added, revoked, or queried.
    
-   Status: Also in the proposal stage and complements ERC 725.
    
---

### ERC 3643 - Security Token Standard

-   Purpose: A standard for creating and managing security tokens on the Ethereum blockchain.
    
-   Features: Provides compliance with regulatory requirements for security tokens, including KYC (Know Your Customer) and AML (Anti-Money Laundering) checks. It also supports complex issuance and transfer restrictions.
    
-   Status: Adopted and used in various security token offerings (STOs)

---

### ERC 1400 - Security Token Standard

-   Purpose: Another standard for security tokens, focused on making them compliant with regulations.
    
-   Features: Combines several ERC standards, including ERC 20, to ensure that security tokens can have features like partitioned balances, forced transfers, and off-chain data (e.g., legal agreements).
    
-   Status: Widely recognized and used in the industry for security tokens.
    

These standards are part of the growing ecosystem of Ethereum proposals aimed at enhancing decentralized identity and compliant tokenization.

“The primary technical distinction between standard ERC-20 tokens and ERC3643 permissioned tokens lies in the conditional nature of the transfer function in ERC3643 tokens. A transaction can only be executed if a decentralized validator approves it, based on the specific governance criteria defined for the token.”

  

“Despite this modification to the transfer function, it's important to note that ERC3643 tokens maintain full compatibility with all ERC-20 based exchanges and tools due to their underlying structure. Integration into an existing ERC-20 compatible platform requires a minor modification: processing pre-checks before any tran sfer to verify the transaction's compliance status with the decentralized validator. If a transaction fails to meet compliance, the platform should provide clear feedback on why it's non-compliant and, where possible, guidance on achieving compliance.”

  
  

[https://github.com/ERC-3643/ERC-3643?tab=readme-ov-file](https://github.com/ERC-3643/ERC-3643?tab=readme-ov-file)

[https://github.com/ERC-3643/ERC-3643/blob/main/contracts/token/Token.sol](https://github.com/ERC-3643/ERC-3643/blob/main/contracts/token/Token.sol)

[https://github.com/onchain-id/solidity](https://github.com/onchain-id/solidity)

[https://docs.onchainid.com/docs/developers/complyDeFi/](https://docs.onchainid.com/docs/developers/complyDeFi/)

  

[https://docs.tokeny.com/docs/general-concept#the-identity-system-for-compliant-digital-assets](https://docs.tokeny.com/docs/general-concept#the-identity-system-for-compliant-digital-assets)

[https://docs.tokeny.com/docs/purpose-architecture-1](https://docs.tokeny.com/docs/purpose-architecture-1)

[https://docs.tokeny.com/docs/identity-sdk](https://docs.tokeny.com/docs/identity-sdk)