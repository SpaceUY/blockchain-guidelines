# Solidity Development Standards & Best Practices

This document outlines recommended Solidity best practices to enhance security, maintainability, and gas efficiency. These guidelines reference common industry standards (OpenZeppelin, Ethereum Security Community) and incorporate naming conventions, code optimization, and Foundry usage tips.

## Language & Compiler

- **Use a Recent Compiler Version**

  - Always specify the Solidity compiler version at the top of each contract file:
    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.17;
    ```
  - Using a recent compiler version ensures you benefit from the latest security checks (e.g., overflow/underflow protection) and language improvements.

- **Lock Pragma**

  - Lock the pragma to a specific compiler minor version (e.g., `^0.8.17`) to avoid mismatches in different build environments.

- **Disable `ABIEncoderV2` if Unnecessary**
  - Since Solidity 0.8, `ABIEncoderV2` is enabled by default. If your code doesn’t need complex data encoding, you can omit the experimental pragma statements.

## Project Structure

A clean structure helps maintain a scalable codebase:

- **`contracts/`**: Where all your Solidity contracts live.
- **`test/`**: Foundry test contracts.
- **`script/`**: Foundry scripts (e.g., deploy scripts, local setup scripts).
- **`lib/`**: External libraries like OpenZeppelin or other third-party code.
- **`foundry.toml`**: Foundry configuration file.

## Contracts Layout

Always keep in mind the official

### File Layout:

1. version
2. imports
3. errors
4. interfaces, libraries, contracts
5. Type declarations
6. State variables
7. Events
8. Modifiers
9. Functions

### Functions Layout:

1. constructor
2. receive function (if exists)
3. fallback function (if exists)
4. external
5. public
6. internal
7. private
8. Within a grouping, place the view and pure functions last

E.g.:

- External
- External view
- External pure

## Naming Conventions

Consistent naming makes your code more readable and auditable:

- **Contracts**

  - Use `CamelCase` for contract names, e.g., `MyToken`, `VotingSystem`.

- **Variables**

  - **Immutable variables**: prefix with `i_`.
    ```solidity
    uint256 immutable i_supplyCap;
    ```
  - **Storage variables**: prefix with `s_`.
    ```solidity
    uint256 private s_totalSupply;
    ```
  - **Local & memory variables**: use `camelCase` (no prefix).
    ```solidity
    uint256 localCounter = 0;
    ```

- **Functions**

  - Use `camelCase` for function names, e.g., `transferTokens()`, `withdrawFunds()`.

- **Constants**

  - Use `UPPER_CASE_WITH_UNDERSCORES` for constants, e.g., `MAX_SUPPLY`, `FEE_RATE`.

- **Events**
  - Use `PascalCase` for event names, e.g., `TransferExecuted`, `TokensMinted`.

## Function Parameters & Memory Usage

- **Use `calldata` for External Function Parameters**

  - When writing external functions, prefer `calldata` for array and string parameters to reduce gas costs and prevent unnecessary copying:
    ```solidity
    function doSomething(address[] calldata users) external {
        // your logic
    }
    ```

- **Use `memory` for Local Copies**
  - If you need to manipulate array or string data inside your function, copy it to a `memory` variable to avoid re-reading from `storage`:
    ```solidity
    function processArray() external {
        uint256[] memory localArray = s_myArray; // read once from storage
        // manipulate localArray...
    }
    ```
  - Minimizing repeated storage reads reduces gas costs.

## Security Practices

- **Checks-Effects-Interactions Pattern**

  - **Checks**: Validate inputs and contract state.
  - **Effects**: Update state variables.
  - **Interactions**: Call external contracts or send ETH last.

  ```solidity
  function withdrawFunds() external {
      // Checks
      require(msg.sender == s_owner, "Not owner");

      // Effects
      uint256 balance = s_balance;
      s_balance = 0;

      // Interactions
      (bool success, ) = s_owner.call{value: balance}("");
      require(success, "Transfer failed");
  }
  ```

- **Reentrancy Protection**

  - Use the OpenZeppelin ReentrancyGuard or apply checks-effects-interactions properly:
    ```solidity
    contract SecureWithdraw is ReentrancyGuard {
        function withdraw() external nonReentrant {
            // ...
        }
    }
    ```

- **Use `require`, `revert`, and Custom Errors**

  - `require` is standard for user input validation.
  - `revert` stops execution and reverts state changes.
  - Custom errors save gas and convey clearer messages:
    ```solidity
    contract SecureWithdraw is ReentrancyGuard {
        function withdraw() external nonReentrant {
            // ...
        }
    }
    ```

- **Avoid Hardcoding Sensitive Data**

  - Do not store private keys or secrets in the contract.
  - For addresses that need to be upgradable or modifiable, store them in `immutable` or `private` variables set via a constructor or setter function.

- **Use Interfaces for External Calls**
  - Interact with external contracts via well-defined `interface` definitions to minimize confusion and potential errors.

## Gas Optimization

- **Use `immutable` for Variables Set in the Constructor**

  - For variables that will not change after deployment, immutable can reduce storage reads:

  ```solidity
  uint256 immutable i_deploymentTimestamp;

  constructor() {
      i_deploymentTimestamp = block.timestamp;
  }
  ```

- **Minimize Storage Writes**

  - Writing to storage is more expensive than reading from it.

- **Use Libraries**
  - Common arithmetic or utility functions can be optimized with libraries to reduce code duplication.

## Code Quality & Style

- **NatSpec Comments**

  - Use Ethereum Natural Specification Format (NatSpec) to document functions, parameters, and return values.
  - Example:

  ```solidity
  /// @notice Transfers tokens from one address to another
  /// @param from The sender's address
  /// @param to The recipient's address
  /// @param amount The amount of tokens to transfer
  /// @return success A boolean indicating if the transfer was successful
  function transfer(
      address from,
      address to,
      uint256 amount
  ) external returns (bool success) {
      // ...
  }
  ```

- **Modifiers**

  - Use modifiers for repeated checks (e.g., `onlyOwner`, `nonReentrant`).
  - Keep them short and focused.

- **Avoid Deep Nesting**

  - Consider early return or splitting logic into smaller functions.

- **DRY Principle (Don’t Repeat Yourself)**

  - Consolidate repeated logic into a single function or library.

- **Inheritance & Interfaces**
  - Inherit from OpenZeppelin Contracts for well-audited, standardized functionality like ERC20, ERC721, and more.

## References

- [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html) - Official Solidity documentation style guide
- [Chainlink Style Guide](https://github.com/smartcontractkit/chainlink-evm/blob/develop/contracts/STYLE_GUIDE.md) - Chainlink's Solidity style guide
- [OpenZeppelin Contracts](https://github.com/OpenZeppelin/openzeppelin-contracts) - Standard secure smart contract implementations
- [Ethereum Smart Contract Best Practices](https://consensys.github.io/smart-contract-best-practices/) - Comprehensive security guidelines
- [Foundry Documentation](https://book.getfoundry.sh/) - Foundry development framework documentation
- [NatSpec Format](https://docs.soliditylang.org/en/latest/natspec-format.html) - Ethereum Natural Specification Format documentation
