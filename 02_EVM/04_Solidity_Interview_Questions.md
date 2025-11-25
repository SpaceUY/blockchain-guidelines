---
title: Solidity Interview Questions
layout: home
parent: Ethereum Virtual Machine
nav_order: 4
---

# Solidity Interview Questions
{: .no_toc }

This section contains a set of interview-level questions that double up as a valuable training and learning resource.

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc .list-style-none}

---

# Easy

## What is the difference between `tx.origin` and `msg.sender`?

**`tx.origin`:**
- The **original EOA (Externally Owned Account)** that initiated the transaction
- Never changes throughout the entire call chain
- Always an EOA, never a contract
- **Unsafe for authorization** — vulnerable to phishing attacks

**`msg.sender`:**
- The **immediate caller** of the current function
- Changes at each step in the call chain
- Can be either an EOA or a contract address
- **Safe for authorization** — use this for access control

**Example:**
```
User (EOA) → Contract A → Contract B
```

Inside Contract B:
- `tx.origin = User` (the original EOA)
- `msg.sender = Contract A` (the immediate caller)

**Why `tx.origin` is unsafe:**

If a malicious contract tricks a user into calling it, it can call your contract with the user's `tx.origin`, bypassing authorization checks:

```solidity
// VULNERABLE - Don't do this!
require(tx.origin == owner, "Not owner");

// SAFE - Do this instead
require(msg.sender == owner, "Not owner");
```

**Best Practice:** Always use `msg.sender` for access control. Never use `tx.origin` for authorization.

---

## What are the available `uint` types in Solidity?

In Solidity, `uint8` is the smallest uint type available, and then all types of the form `uint(8*n)` are valid: `uint16`, `uint24`, `uint32`, ..., up to `uint256` (in increments of 8 bits).

The simple `uint` is an alias for `uint256`.

**Note**: Smaller types like `uint8` or `uint128` don't automatically save gas unless they're **packed together** in storage. The EVM operates on 32-byte words, so smaller types still consume a full word in memory and on the stack. Storage packing only occurs when multiple variables fit in the same 32-byte storage slot.

**Corresponding signed types**: `int8`, `int16`, ..., `int256` (and `int` as an alias for `int256`) follow the same pattern.

---

## Describe Solidity's primitive types

Solidity's primitive (value) types are stored directly in variables, not by reference:

| Type | Description | Range/Size | Example |
|------|-------------|------------|---------|
| **`bool`** | Boolean | `true` or `false` | `bool isActive = true;` |
| **`uint`** | Unsigned integer | `uint8` to `uint256` (8-bit increments) | `uint256 count = 100;` |
| **`int`** | Signed integer | `int8` to `int256` (8-bit increments) | `int256 balance = -50;` |
| **`address`** | Ethereum address | 20 bytes | `address owner = 0x123...;` |
| **`address payable`** | Address that can receive Ether | 20 bytes | `address payable recipient;` |
| **`bytes1` to `bytes32`** | Fixed-size byte array | 1-32 bytes | `bytes32 hash;` |
| **`enum`** | User-defined type | Underlying uint8 | `enum Status { Pending, Active }` |

**Key characteristics:**

```solidity
contract Primitives {
    // Booleans
    bool public isComplete = false;
    
    // Integers (default: 0)
    uint256 public count;           // 0 to 2^256-1
    int256 public temperature = -10; // -(2^255) to 2^255-1
    
    // Addresses
    address public owner;
    address payable public recipient;
    
    // Fixed bytes (more gas-efficient than dynamic bytes for small data)
    bytes32 public hash;
    bytes1 public flag;
    
    // Enums (improves readability)
    enum State { Created, Locked, Inactive }
    State public state = State.Created;
}
```

**Important notes:**
- **Default values**: All primitives have defaults (`0`, `false`, `address(0)`)
- **Value types**: Copying creates independent copies (not references)
- **No `null`/`undefined`**: Uninitialized variables have default values, not null

**Not primitives** (reference types): `string`, `bytes` (dynamic), `array`, `mapping`, `struct` 

---

## What is the difference between `fallback` and `receive`?

Both are special functions that handle unexpected calls to a contract, but they're triggered in different scenarios:

**`receive()`:**
- Executed when a call has **empty calldata** (no data, no function selector)
- Specifically for **plain Ether transfers** (e.g., via `.send()`, `.transfer()`, or low-level `call` with no data)
- Must be marked `external payable`
- Can only have one per contract
- More gas-efficient for simple Ether receipts

**`fallback()`:**
- Executed when:
  - No function signature matches the calldata, OR
  - No `receive()` function exists and Ether is sent with empty calldata
- Acts as a **catch-all** for unmatched function calls
- Can be `payable` or non-payable (non-payable will reject Ether)
- Can only have one per contract
- Used for proxy patterns and custom call routing

**Execution Flow:**

```
Ether sent to contract
         |
    Has calldata?
    /           \
  YES            NO
   |              |
fallback()    receive() exists?
               /        \
             YES         NO
              |           |
          receive()   fallback()
```

**Example:**

```solidity
contract Receiver {
    event Received(address sender, uint amount);
    event Fallback(address sender, uint amount, bytes data);
    
    // Called for plain ETH transfers
    receive() external payable {
        emit Received(msg.sender, msg.value);
    }
    
    // Called for all other cases
    fallback() external payable {
        emit Fallback(msg.sender, msg.value, msg.data);
    }
}

// Usage:
// address(receiver).call{value: 1 ether}("")           → receive()
// address(receiver).call{value: 1 ether}("0x1234...")  → fallback()
// receiver.nonExistentFunction()                       → fallback()
```

**Best Practice:** 
- Implement `receive()` if you want to accept plain Ether transfers
- Implement `fallback()` for proxy patterns or to handle unmatched function calls
- Keep both functions simple and gas-efficient to avoid out-of-gas errors (especially with `.transfer()` and `.send()` which forward only 2300 gas)

---

## What is the difference between `immutable` and `constant`?

Both create **unchangeable** variables, but they differ in when values are set and how they're stored:

| Feature | `constant` | `immutable` |
|---------|------------|-------------|
| **Set at** | Compile-time | Deploy-time (constructor) |
| **Value** | Must be literal or expression | Can use constructor parameters |
| **Storage** | Not stored - inlined in bytecode | Stored in bytecode (not storage slots) |
| **Gas cost** | Cheapest (direct value substitution) | Cheap (no SLOAD, just bytecode read) |

**Example:**

```solidity
contract Example {
    // Constant - value must be known at compile time
    uint256 public constant MAX_SUPPLY = 1_000_000;
    address public constant WETH = 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2;
    
    // Immutable - value set once in constructor
    address public immutable owner;
    uint256 public immutable deployTime;
    
    constructor(address _owner) {
        owner = _owner;           // Can use constructor parameters
        deployTime = block.timestamp;  // Can use runtime values
    }
}
```

**When to use:**
- **`constant`**: Fixed values known at compile time (addresses, max values, mathematical constants)
- **`immutable`**: Values determined at deployment but never change after (owner, paired token, deployment timestamp)

**Key benefit:** Both avoid expensive storage reads (~2100 gas for cold SLOAD), making them much cheaper than regular state variables.

---

## What are the different visibility modifiers in Solidity?

Visibility modifiers control who can call functions or access state variables:

| Modifier | Accessible From | Gas Cost | Use For |
|----------|----------------|----------|---------|
| **`public`** | Anywhere (internal + external) | Higher | General-purpose functions |
| **`external`** | Only outside contract | Lower | External-only functions (uses calldata) |
| **`internal`** | Same contract + derived | N/A | Helper functions, inheritance |
| **`private`** | Only same contract | N/A | Internal implementation details |

**Key differences:**

```solidity
contract Visibility {
    uint256 private secretValue;      // Only this contract
    uint256 internal sharedValue;     // This + child contracts
    uint256 public publicValue;       // Auto getter created
    
    // External - cheapest for external calls (uses calldata)
    function externalFunc(uint[] calldata data) external pure returns (uint) {
        return data[0];
    }
    
    // Public - can call internally or externally (more expensive)
    function publicFunc(uint[] memory data) public pure returns (uint) {
        return data[0];
    }
    
    // Internal - only from this contract or children
    function internalHelper() internal pure returns (uint) {
        return 42;
    }
    
    // Private - only from this contract
    function privateHelper() private pure returns (uint) {
        return 99;
    }
}
```

**Important notes:**
- **`external` vs `public`**: External saves gas (~20-40) by using `calldata` instead of copying to `memory`
- **`private` ≠ secret**: All blockchain data is public; `private` only restricts Solidity access
- **State variables**: Can be `public`, `internal`, or `private` (not `external`)

**Best Practice:** Use `external` for functions only called externally—it's cheaper!

---

## What is a `payable` function?

A `payable` function is a function that **can receive Ether** when called. Without the `payable` modifier, a function will automatically **reject** any transaction that sends Ether to it.

**Key characteristics:**

- **Accepts Ether**: The function can receive ETH via `msg.value`
- **No automatic rejection**: Transactions with ETH attached won't revert
- **Required for receiving**: Must be used for any function that should handle incoming Ether

**Common use cases:**

- Payment functions (purchases, deposits, donations)
- Contract funding mechanisms
- Fallback and receive functions for accepting direct transfers

**Example:**

```solidity
contract PaymentProcessor {
    mapping(address => uint256) public balances;
    
    // payable function - accepts ETH
    function deposit() public payable {
        require(msg.value > 0, "Must send ETH");
        balances[msg.sender] += msg.value;
    }
    
    // non-payable function - rejects ETH
    function withdraw(uint256 amount) public {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }
}
```

**Important notes:**

- Calling a non-payable function with ETH attached will cause the transaction to **revert**
- The `payable` modifier is also used for address types: `address payable` can receive Ether via `.transfer()` or `.send()`
- `fallback()` and `receive()` functions should typically be marked `payable` to accept direct Ether transfers

---

## What is the effect on gas of making a function payable?

Marking a function `payable` makes it **slightly cheaper** to call because the compiler skips the `msg.value == 0` check automatically inserted for non-payable functions.

**Why?**
- When a function is **not payable**, the EVM must verify that **no Ether was sent**. If Ether is attached, it reverts — that extra check costs gas.
- With `payable`, the function accepts ETH directly, so there's no need for that safety check, saving a few gas units (~20-40 gas per call).

**Trade-off**: Only use `payable` when the function legitimately needs to accept Ether, or when the gas savings matter and you're certain no Ether should be sent.

---

## What is the difference between `assert`, `require`, and `revert`?

**`require(condition, "message")`:**
- **Purpose**: Input validation and business logic checks
- **Gas**: Refunds remaining gas on failure
- **Use for**: User errors, preconditions, external input validation
- **Example**: `require(balance >= amount, "Insufficient balance")`

**`assert(condition)`:**
- **Purpose**: Internal invariants and bug detection
- **Gas**: Burns ALL remaining gas (pre-0.8.0 behavior; post-0.8.0 refunds like require)
- **Use for**: Conditions that should **never** fail if code is correct
- **Example**: `assert(totalSupply >= balance)` (mathematical invariant)

**`revert("message")` / `revert CustomError()`:**
- **Purpose**: Explicit revert with more control (alternative to `require`)
- **Gas**: Refunds remaining gas
- **Use for**: Complex conditional logic, custom error handling
- **More flexible**: Works with `if` statements for complex conditions

**Gas Optimization (Solidity ≥0.8.4):**

Custom errors are **~50% cheaper** than string messages:

```solidity
error InsufficientBalance(uint256 available, uint256 required);

// Expensive (string)
require(balance >= amount, "Insufficient balance");

// Cheap (custom error) - Solidity 0.8.26+
require(balance >= amount, InsufficientBalance());

// Cheap (custom error) - All versions ≥0.8.4
if (balance < amount) {
    revert InsufficientBalance(balance, amount);
}
```

**Best Practice:**
- Use `require()` for user-facing validation
- Use `assert()` only for invariants that should never fail
- Use `revert()` with custom errors for better gas efficiency and debugging
- Modern Solidity (≥0.8.26): `require()` supports custom errors directly

---

## What is the difference between `view` and `pure`?

These are state mutability modifiers that restrict what a function can do:

**`view`:**
- **Can read** blockchain state (storage variables, other contracts' state, balance, block data, etc.)
- **Cannot modify** state or send Ether
- Promises not to change anything, only observe

**`pure`:**
- **Cannot read or modify** blockchain state
- Only works with function parameters and local variables
- Pure computation only — no external dependencies

**Gas Costs:**
- **Off-chain calls** (via `eth_call`): Both are **free** — executed locally by your node
- **On-chain calls** (from another transaction): Both **cost gas** when called internally, as they're part of transaction execution

**When to use:**
- Use `view` when you need to read state (e.g., `balanceOf`, getter functions)
- Use `pure` for utility/helper functions that only compute values (e.g., hash functions, math operations)

**Example:**
```solidity
uint256 public totalSupply;

// view - reads state
function getTotalSupply() public view returns (uint256) {
    return totalSupply;
}

// pure - no state access
function add(uint256 a, uint256 b) public pure returns (uint256) {
    return a + b;
}
```

---

## What is a modifier and what does it do?

A **modifier** is a reusable piece of code that can be attached to functions to add preconditions, postconditions, or wrapped logic. It helps avoid code repetition (DRY principle).

**Key concepts:**

- The special `_` placeholder represents where the **function body** executes
- Code before `_` runs **before** the function
- Code after `_` runs **after** the function
- Modifiers can accept parameters like functions
- Multiple modifiers can be chained on a single function

**Common use cases:**
- Access control (only owner, only admin)
- Input validation
- State checks (contract not paused)
- Reentrancy guards

**Example:**

```solidity
contract Owned {
    address public owner;
    
    constructor() {
        owner = msg.sender;
    }
    
    // Modifier with precondition
    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner");
        _; // Function body executes here
    }
    
    // Modifier with parameter
    modifier validAddress(address addr) {
        require(addr != address(0), "Invalid address");
        _;
    }
    
    // Modifier with before/after logic
    modifier pausable() {
        require(!paused, "Contract is paused");
        _; // Function runs
        emit ActionCompleted(); // Runs after function
    }
    
    // Using modifiers
    function transferOwnership(address newOwner) 
        public 
        onlyOwner                    // First modifier
        validAddress(newOwner)       // Second modifier (with parameter)
    {
        owner = newOwner;
    }
}
```

**Execution order with multiple modifiers:**

```solidity
function foo() mod1 mod2 mod3 { ... }

// Executes as:
// mod1 (before _)
//   mod2 (before _)
//     mod3 (before _)
//       function body
//     mod3 (after _)
//   mod2 (after _)
// mod1 (after _)
```

**Best Practice:** Use modifiers for repeated checks, but keep them simple. Complex logic should be in separate functions for better testability and readability.

---

## What is `abi.encodePacked` and what is its utility?

`abi.encodePacked` performs **non-standard packed encoding** by tightly packing arguments without padding them to 32 bytes, and removing length prefixes for dynamic types (strings, bytes, arrays).

**Utility:**
- **Gas savings**: More compact encoding means less calldata (cheaper transactions)
- **Shorter hashes**: Useful when you need deterministic hashing of concatenated values
- Common use cases: Creating unique IDs, commitment schemes, signature message construction

**Security Warning - Hash Collisions:**

`abi.encodePacked` is **vulnerable to hash collisions** with dynamic types because it removes length information.

**Example:**
```solidity
// These produce the SAME hash!
keccak256(abi.encodePacked("aa", "bb"))  // 0x...
keccak256(abi.encodePacked("a", "abb"))  // 0x... (same!)
```

**Safe**: Static types (e.g., `uint256`, `address`) — they're padded to 32 bytes with no ambiguity.

**Risky**: Dynamic types (strings, bytes, arrays) in security-critical contexts:
- Signature verification
- Merkle proofs
- Access control checks
- Token ID generation

**Best Practice**: Use `abi.encode` (includes length prefixes) for hashing, or ensure only static types are used with `abi.encodePacked`

---

## What's the difference between storage, memory, and calldata?

These are **data location** keywords that specify where variables are stored:

| Location | Lifetime | Cost | Mutability | Usage |
|----------|----------|------|------------|-------|
| **`storage`** | Persistent (blockchain) | Very expensive | Mutable | State variables |
| **`memory`** | Temporary (execution) | Moderate | Mutable | Function parameters, local variables |
| **`calldata`** | Temporary (execution) | Cheapest | **Immutable** | External function parameters only |

**Key differences:**

- **`storage`**: Data persists between function calls and transactions. Modifying costs gas.
- **`memory`**: Created fresh per function call, discarded after execution. Cannot be used for state variables.
- **`calldata`**: Read-only copy of function arguments. Saves gas vs `memory` for external functions.

**Example:**

```solidity
contract DataLocations {
    uint[] public numbers; // storage (state variable)
    
    // calldata - cheapest for external, read-only
    function processExternal(uint[] calldata data) external pure returns (uint) {
        return data[0]; // Cannot modify data
    }
    
    // memory - needed if you modify the array
    function processPublic(uint[] memory data) public pure returns (uint) {
        data[0] = 99; // Can modify
        return data[0];
    }
    
    function addToStorage(uint value) public {
        numbers.push(value); // Modifies storage
    }
}
```

**Best Practice:** Use `calldata` for `external` function parameters when you don't need to modify them—it's cheaper than `memory`.

---

## What are Events and what are they useful for?

**Events** are logs emitted by smart contracts that are stored in the transaction receipt, not in contract storage. They're **cheap** to emit and enable external applications to track on-chain activity.

**Key uses:**
- **Frontend updates**: Listen to events via WebSocket/RPC to update UI in real-time
- **Indexing/querying**: Services like The Graph index events for efficient querying
- **Audit trail**: Permanent log of contract activity (cheaper than storage)
- **Off-chain triggers**: Backend services can react to on-chain events

**Indexed parameters:**

Up to **3 parameters** can be marked `indexed`, making them searchable/filterable via RPC:

```solidity
event Transfer(
    address indexed from,    // Searchable
    address indexed to,      // Searchable
    uint256 value            // Not searchable, but still logged
);

// Query via RPC: "Get all Transfer events where from = 0x123..."
```

**How to retrieve events:**

```javascript
// Via ethers.js
const filter = contract.filters.Transfer(fromAddress, null);
const events = await contract.queryFilter(filter, fromBlock, toBlock);

// Via raw RPC (eth_getLogs)
const logs = await provider.send("eth_getLogs", [{
  address: contractAddress,
  topics: [transferEventTopic, fromAddressEncoded],
  fromBlock: "0x0",
  toBlock: "latest"
}]);
```

**Cost:** ~375 gas per indexed parameter + ~375 gas base + data cost. Much cheaper than storage (~20,000 gas per slot).

**Limitation:** Events are not accessible from within smart contracts—only via external queries.

---

## What is ABI encoding?

**ABI (Application Binary Interface) encoding** is how Solidity encodes function calls and data into bytes for the EVM. It defines how to pack parameters into calldata and how to decode return values.

**Common encoding functions:**

| Function | Purpose | Padding |
|----------|---------|---------|
| `abi.encode()` | Standard encoding with 32-byte padding | ✅ Full |
| `abi.encodePacked()` | Tight packing, no padding | ❌ Minimal |
| `abi.encodeWithSelector()` | Encode with 4-byte function selector | ✅ Full |
| `abi.encodeWithSignature()` | Encode with function signature string | ✅ Full |
| `abi.decode()` | Decode bytes into typed variables | N/A |

**Example:**

```solidity
function demonstrateABI() public pure {
    // Standard encoding (padded to 32 bytes)
    bytes memory encoded = abi.encode(uint8(5), address(0x123));
    // Result: 0x0000...0005 (32 bytes) + 0x0000...0123 (32 bytes)
    
    // Packed encoding (tight, no padding)
    bytes memory packed = abi.encodePacked(uint8(5), address(0x123));
    // Result: 0x05 (1 byte) + 0x0000...0123 (20 bytes) = 21 bytes
    
    // Encode function call
    bytes memory callData = abi.encodeWithSignature(
        "transfer(address,uint256)",
        recipient,
        amount
    );
    // Result: 0xa9059cbb (selector) + encoded parameters
    
    // Decode
    (uint256 a, address b) = abi.decode(encoded, (uint256, address));
}
```

**Use cases:**
- **`abi.encode`**: Safe for hashing, passing data between contracts
- **`abi.encodePacked`**: Gas-efficient hashing (watch for collisions)
- **`abi.encodeWithSelector`**: Low-level contract calls
- **`abi.decode`**: Parse return data from external calls

**Key point:** ABI encoding ensures type safety and consistent data layout across the Ethereum ecosystem.

---

# Medium

## What is an interface in Solidity?

An **interface** defines a contract's external functions without implementation, providing a **clean, type-safe way** to interact with external contracts. It wraps low-level ABI encoding/decoding into readable function calls.

**Key benefits:**

1. **Cleaner code**: Use familiar function syntax instead of `abi.encodeWithSignature`
2. **Type safety**: Compiler checks parameters and return types
3. **No implementation**: Only function signatures, no state variables or logic
4. **Implicit `external`**: All functions are automatically external

**Example - With vs Without Interface:**

```solidity
// ❌ Without interface - manual ABI encoding
contract ManualCall {
    function transferTokens(address token, address to, uint256 amount) external {
        // Messy, error-prone, no type checking
        (bool success, ) = token.call(
            abi.encodeWithSignature("transfer(address,uint256)", to, amount)
        );
        require(success);
    }
}

// ✅ With interface - clean and type-safe
interface IERC20 {
    function transfer(address to, uint256 amount) external returns (bool);
    function balanceOf(address account) external view returns (uint256);
}

contract CleanCall {
    function transferTokens(address token, address to, uint256 amount) external {
        // Clean, readable, compiler-checked
        IERC20(token).transfer(to, amount);
    }
}
```

**Under the hood:** The compiler automatically converts `IERC20(token).transfer(to, amount)` into the ABI-encoded call, but with full type safety.

**Rules:**
- Cannot have state variables
- Cannot have constructors
- Cannot inherit from contracts (only other interfaces)
- All functions must be external (implicitly)

**Best Practice:** Always use interfaces for external contract interactions—they make code cleaner, safer, and more maintainable.

---

## What is a library in Solidity?

A **library** is a reusable contract deployed once and used by multiple contracts via `DELEGATECALL`. Libraries provide common functionality without duplicating code.

**Key characteristics:**

| Feature | Libraries | Regular Contracts |
|---------|-----------|-------------------|
| **State** | No state variables (stateless) | Can have state |
| **Deployment** | Once, reused by many | Per contract |
| **Call method** | `DELEGATECALL` | `CALL` |
| **`this`** | Cannot use | Can use |
| **Inheritance** | Cannot inherit or be inherited | Full inheritance |

**Two usage patterns:**

```solidity
// 1. Direct call
library Math {
    function add(uint a, uint b) internal pure returns (uint) {
        return a + b;
    }
}

contract UseLibrary {
    function calculate() public pure returns (uint) {
        return Math.add(5, 10); // Direct library call
    }
}

// 2. Using for (attach to types)
library SafeMath {
    function add(uint a, uint b) internal pure returns (uint) {
        uint c = a + b;
        require(c >= a, "Overflow");
        return c;
    }
}

contract UseUsingFor {
    using SafeMath for uint;
    
    function calculate(uint a, uint b) public pure returns (uint) {
        return a.add(b); // Cleaner syntax!
    }
}
```

**Benefits:**
- **Gas efficiency**: Deploy once, use everywhere (no code duplication)
- **Code reuse**: Share utilities across projects (OpenZeppelin, etc.)
- **Clean syntax**: `using for` makes code more readable

**Common examples:** SafeMath, Address utilities, String manipulation, Math operations

**Note:** Libraries with `internal` functions get embedded in contract bytecode (no DELEGATECALL). Only `public`/`external` functions require deployment.

---

## What is an abstract contract?

An **abstract contract** has at least one function declared but not implemented. It **cannot be deployed** directly—only used as a base for inheritance.

**Key points:**
- Marked with `abstract` keyword
- Contains unimplemented functions (no body)
- Must be inherited and implemented by child contracts
- Can have both implemented and unimplemented functions

**Example:**

```solidity
// Abstract - cannot deploy
abstract contract Base {
    function getName() public pure virtual returns (string memory);  // No implementation
    
    function greet() public pure returns (string memory) {
        return string.concat("Hello, ", getName());  // Can use unimplemented function
    }
}

// Concrete - can deploy
contract Child is Base {
    function getName() public pure override returns (string memory) {
        return "Alice";  // Must implement
    }
}
```

**vs Interface:** Interfaces have zero implementation; abstract contracts can have partial implementation.

**Use case:** Share common logic while forcing child contracts to implement specific functions.

---

## What is a DELEGATECALL?

`DELEGATECALL` is a low-level function that executes another contract's code **in the caller's storage context**.

**Key difference from `CALL`:**

| Aspect | `CALL` | `DELEGATECALL` |
|--------|--------|----------------|
| **Storage** | Target contract's storage | Caller's storage |
| **msg.sender** | Changes to caller | Stays original sender |
| **msg.value** | Changes | Stays original value |
| **Use case** | External calls | Libraries, proxies |

**Visual:**

```
User → Proxy.delegatecall(Implementation)
       ↓ Runs Implementation code
       ↓ But uses Proxy's storage
       → Proxy's state changes
```

**Common use:**
- **Proxy patterns**: Logic in implementation, state in proxy
- **Libraries**: Reusable code without deployment duplication

**Security warning:** `delegatecall` gives full storage access. Only use with trusted contracts—malicious code can corrupt all state.

**Example:**

```solidity
// Library pattern
library Math {
    function add(uint a, uint b) internal pure returns (uint) {
        return a + b;
    }
}

// Proxy pattern
contract Proxy {
    address implementation;
    
    fallback() external payable {
        address impl = implementation;
        assembly {
            // Delegate to implementation
            let result := delegatecall(gas(), impl, 0, calldatasize(), 0, 0)
            // Return data
            returndatacopy(0, 0, returndatasize())
            switch result
            case 0 { revert(0, returndatasize()) }
            default { return(0, returndatasize()) }
        }
    }
}
```

---

## Can you explain how storage is laid out in a contract?

**Storage layout** determines how state variables are stored in 32-byte slots (0, 1, 2, ...). Understanding this is crucial for gas optimization.

**Basic rules:**

1. **Sequential allocation**: Variables assigned slots in declaration order
2. **Packing**: Multiple small variables (< 32 bytes) pack into same slot if they fit
3. **New slot triggers**: Variables > remaining slot space start a new slot
4. **Structs/arrays**: Always start fresh slot (even if space remains)

**Layout example:**

```solidity
contract StorageLayout {
    // Slot 0: packed together (1 + 1 + 20 = 22 bytes < 32)
    uint8 a;        // 1 byte
    uint8 b;        // 1 byte  
    address c;      // 20 bytes
    
    // Slot 1: new slot (uint256 = 32 bytes)
    uint256 d;
    
    // Slot 2-3: packed together (8 + 8 = 16 bytes)
    uint64 e;       // 8 bytes
    uint64 f;       // 8 bytes
    // 16 bytes free in slot 2
    
    // Slot 4: struct starts new slot
    struct Data {
        uint256 x;  // Slot 4
        uint128 y;  // Slot 5 (first 16 bytes)
    }
    Data data;
    
    // Slot 6: arrays/mappings use keccak256 hashing
    uint256[] dynamicArray;      // Slot 6 stores length
    mapping(address => uint) m;  // Slot 7 (empty, values at keccak256(key . 7))
}
```

**Special cases:**

**Mappings:**
- Slot stores nothing (placeholder)
- Actual value at: `keccak256(abi.encode(key, slot))`

**Dynamic arrays:**
- Slot stores length
- Elements at: `keccak256(slot) + index`

**Fixed arrays:**
- Elements stored sequentially, packing applies

**Gas optimization tips:**

```solidity
// ❌ Bad - 3 slots (96 gas writes)
uint8 a;      // Slot 0
uint256 b;    // Slot 1
uint8 c;      // Slot 2

// ✅ Good - 2 slots (64 gas writes)
uint8 a;      // Slot 0
uint8 c;      // Slot 0 (packed)
uint256 b;    // Slot 1
```

**Pro tip:** Use `forge inspect ContractName storage-layout` to visualize actual layout!

---

## What is the checks-effects-interactions pattern?

The **Checks-Effects-Interactions (CEI)** pattern is a defensive programming practice that prevents **reentrancy attacks** by ordering operations in a specific sequence:

**1. Checks**: Validate all conditions first
   - Verify balances, permissions, requirements
   - `require()` statements, input validation

**2. Effects**: Update internal state
   - Modify storage variables, balances, mappings
   - Change contract state before any external calls

**3. Interactions**: Call external contracts last
   - Send Ether, call other contracts, emit events
   - Any operation that transfers control

**Why it works:**

If an external contract reenters during step 3, the state has **already been updated** in step 2, preventing double-withdrawal or balance manipulation.

**Example - Vulnerable vs Safe:**

```solidity
// ❌ VULNERABLE - Interaction before Effect
function withdrawBad(uint amount) public {
    require(balances[msg.sender] >= amount);
    (bool success, ) = msg.sender.call{value: amount}(""); // Interaction
    require(success);
    balances[msg.sender] -= amount; // Effect (TOO LATE!)
}

// ✅ SAFE - CEI Pattern
function withdrawGood(uint amount) public {
    // 1. Checks
    require(balances[msg.sender] >= amount, "Insufficient balance");
    
    // 2. Effects
    balances[msg.sender] -= amount;
    
    // 3. Interactions
    (bool success, ) = msg.sender.call{value: amount}("");
    require(success, "Transfer failed");
}
```

**Best Practice:** Always follow CEI pattern, or use OpenZeppelin's [ReentrancyGuard](https://docs.openzeppelin.com/contracts/4.x/api/security#reentrancyguard) for additional protection.

---

## What is function overloading and why does it work in Solidity?

**Function overloading** allows multiple functions with the same name but different parameter types to coexist in a contract.

**Why it works:** Function selectors are calculated from the **full function signature** (name + parameter types), not just the name:

```solidity
contract Example {
    // Different selectors despite same name
    function transfer(address to) public {
        // Selector: 0x1a695230 = keccak256("transfer(address)")[:4]
    }
    
    function transfer(address to, uint256 amount) public {
        // Selector: 0xa9059cbb = keccak256("transfer(address,uint256)")[:4]
    }
    
    function transfer(address to, uint256 amount, bytes memory data) public {
        // Selector: 0xbeabacc8 = keccak256("transfer(address,uint256,bytes)")[:4]
    }
}
```

Each has a **unique 4-byte selector**, so the EVM can distinguish them when routing calls.

**Utility:**
- **Convenience:** Same logical operation, different interfaces (e.g., with/without optional parameters)
- **Flexibility:** Default values without explicit defaults (not supported in older Solidity)
- **Common patterns:** Widely used in token standards (ERC20, ERC721) for variations like `safeTransferFrom`

**Note:** Return types don't affect selectors—only parameter types matter. Functions with the same name and parameters but different return types cause a compilation error.

---

## What is frontrunning?

**Frontrunning** is when an attacker sees your pending transaction in the mempool and submits a similar transaction with higher gas to get it included in a block first, profiting from your action.

**Example:**
You submit a DEX buy order → Bot sees it → Bot buys first (driving price up) → Your transaction executes at worse price → Bot profits.

**Why it works:** Public mempool + validators prioritize higher gas fees

**Mitigation strategies:**

1. **Commit-Reveal Scheme:** Hash your intent first, reveal later
   ```solidity
   // Phase 1: Commit
   commit(keccak256(abi.encodePacked(secret, salt)));
   
   // Phase 2: Reveal (after delay)
   reveal(secret, salt); // Contract verifies hash
   ```

2. **Private Transactions:** [Flashbots Protect](https://docs.flashbots.net/flashbots-protect/overview), private RPCs

3. **MEV Protection:** Use MEV-resistant protocols or private transaction pools

---

## What is the approval pattern in ERC20? How do `approve`, `allowance`, and `transferFrom` work together?

The **approval pattern** is ERC20's permission system that separates **authorization** from **execution**, allowing third parties (like DEXs) to spend tokens on your behalf.

**The three functions:**

| Function | Purpose | Called By |
|----------|---------|-----------|
| `approve(spender, amount)` | Grant permission to spend | Token owner |
| `allowance(owner, spender)` | Check approved amount | Anyone (view) |
| `transferFrom(from, to, amount)` | Execute transfer using allowance | Approved spender |

**How it works:**

```solidity
// 1. Owner approves spender (e.g., Uniswap contract)
token.approve(uniswapRouter, 1000 * 10**18);

// 2. Anyone can check the allowance
uint256 allowed = token.allowance(owner, uniswapRouter);

// 3. Spender uses transferFrom to move tokens
// (Called by Uniswap router, not owner)
token.transferFrom(owner, recipient, 500 * 10**18);
```

**Example implementation:**

```solidity
contract ERC20 {
    mapping(address => uint256) public balanceOf;
    mapping(address => mapping(address => uint256)) public allowance;
    
    function approve(address spender, uint256 amount) public returns (bool) {
        allowance[msg.sender][spender] = amount;
        emit Approval(msg.sender, spender, amount);
        return true;
    }
    
    function transferFrom(address from, address to, uint256 amount) 
        public returns (bool) 
    {
        require(allowance[from][msg.sender] >= amount, "Insufficient allowance");
        allowance[from][msg.sender] -= amount;
        balanceOf[from] -= amount;
        balanceOf[to] += amount;
        emit Transfer(from, to, amount);
        return true;
    }
}
```

**Common use cases:**
- **DEXs**: Approve router to swap your tokens
- **Staking**: Approve staking contract to lock tokens
- **Payment processors**: Approve contracts to pull payments

**Security consideration:** Approving `type(uint256).max` is common but risky—contracts have unlimited access until revoked. Better to approve only what's needed.

---

## What is the difference between `transferFrom` and `safeTransferFrom` in the ERC721 standard?

Both transfer NFTs from one address to another, but with different safety guarantees:

**`transferFrom(from, to, tokenId)`:**
- Transfers the NFT with **no safety checks**
- Works for both EOAs and contracts
- **Risk**: NFT can be permanently locked if sent to a contract that can't handle it
- Faster and cheaper (no callback)

**`safeTransferFrom(from, to, tokenId)`:**
- Transfers the NFT **with receiver validation**
- If `to` is a contract, it **must implement `onERC721Received()`** and return the correct selector
- **Prevents**: NFTs from being locked in incompatible contracts
- Slightly more expensive (callback overhead)

**When `safeTransferFrom` succeeds/fails:**

| Receiver Type | Result | Why |
|---------------|--------|-----|
| **EOA (wallet)** | ✅ Always succeeds | No callback needed |
| **Contract with `onERC721Received()`** | ✅ Succeeds | Returns correct selector |
| **Contract without `onERC721Received()`** | ❌ Reverts | Missing required function |
| **Contract with wrong signature** | ❌ Reverts | Invalid function signature |
| **`onERC721Received()` reverts** | ❌ Reverts | Callback logic fails |

**Example:**

```solidity
// ❌ Unsafe - NFT could be locked forever
nft.transferFrom(from, unknownContract, tokenId);

// ✅ Safe - Ensures receiver can handle NFT
nft.safeTransferFrom(from, unknownContract, tokenId);
```

**Best Practice:** Use `safeTransferFrom` by default unless you have a specific reason to use `transferFrom` (e.g., gas optimization when receiver is known to be safe).

---

## What is ERC-1155 and how does it differ from ERC-20 and ERC-721?

**ERC-1155** is the **Multi-Token Standard** that can represent multiple token types (fungible, non-fungible, or semi-fungible) in a single contract.

**Key differences:**

| Feature | ERC-20 | ERC-721 | ERC-1155 |
|---------|--------|---------|----------|
| **Token types** | Fungible only | NFTs only | Both + semi-fungible |
| **Contract per type** | Yes | Yes | No (all in one) |
| **Batch operations** | ❌ | ❌ | ✅ Built-in |
| **Gas efficiency** | Lower | Lower | Higher (batch transfers) |
| **Use case** | Currencies | Unique items | Gaming, multi-asset systems |

**Core functions:**

```solidity
interface IERC1155 {
    // Single transfer
    function safeTransferFrom(address from, address to, uint256 id, uint256 amount, bytes data) external;
    
    // Batch transfer (gas efficient!)
    function safeBatchTransferFrom(address from, address to, uint256[] ids, uint256[] amounts, bytes data) external;
    
    // Balance of specific token ID
    function balanceOf(address account, uint256 id) external view returns (uint256);
    
    // Batch balance check
    function balanceOfBatch(address[] accounts, uint256[] ids) external view returns (uint256[]);
}
```

**Example use case - Gaming:**

```solidity
contract GameItems is ERC1155 {
    uint256 public constant GOLD = 0;      // Fungible currency
    uint256 public constant SWORD = 1;     // Semi-fungible item
    uint256 public constant HERO_1 = 100;  // Unique NFT
    
    // One contract, multiple token types!
    // Player has: 500 GOLD, 3 SWORDs, 1 HERO_1
}
```

**Advantages:**
- **Gas savings**: Batch transfer 100 items in one transaction
- **Simplified management**: One contract for entire game economy
- **Atomic swaps**: Trade multiple items atomically

**Best Practice:** Use ERC-1155 for systems with multiple asset types (games, marketplaces with bundles).

---

## What is ERC-4626 (Tokenized Vault Standard)?

**ERC-4626** standardizes **yield-bearing vaults** where users deposit assets and receive shares representing their claim on the vault's growing balance.

**Core concept:** Deposit asset → Get shares → Shares increase in value as vault earns yield

**Key functions:**

| Function | Purpose |
|----------|---------|
| `deposit(assets, receiver)` | Deposit assets, receive shares |
| `mint(shares, receiver)` | Mint exact shares, pull assets |
| `withdraw(assets, receiver, owner)` | Burn shares, receive assets |
| `redeem(shares, receiver, owner)` | Burn exact shares, receive assets |
| `convertToShares(assets)` | Preview shares for assets |
| `convertToAssets(shares)` | Preview assets for shares |

**Example:**

```solidity
interface IERC4626 {
    function asset() external view returns (address);  // Underlying token (e.g., USDC)
    
    function deposit(uint256 assets, address receiver) 
        external returns (uint256 shares);
    
    function withdraw(uint256 assets, address receiver, address owner) 
        external returns (uint256 shares);
    
    function totalAssets() external view returns (uint256);  // Total underlying
}

// User deposits 100 USDC → receives 100 shares
// Vault earns yield → now 110 USDC in vault
// User's 100 shares → worth 110 USDC
```

**Why it matters:**
- **Composability**: All vaults use same interface (Yearn, Aave, Compound, etc.)
- **DeFi legos**: Easy to build on top of any compliant vault
- **No integration hell**: One interface works everywhere

**Use cases:**
- Yield aggregators (Yearn)
- Lending protocols (Aave, Compound)
- Liquidity mining vaults
- Automated strategies

**Best Practice:** Implement ERC-4626 for any yield-generating contract to maximize composability.

---

## What is a signature replay attack?

A **signature replay attack** occurs when a valid signature is reused in an unintended context (different chain, contract, or transaction) to repeat an action without consent.

**Why it works:** Signatures only prove data was signed, not where or when it should be used. Without context binding, attackers can replay the same signature.

**Examples:**
- Replaying `permit()` on another token deployment
- Reusing meta-transactions on forked chains  
- Resubmitting signatures without nonce tracking

**Prevention:**

| Method | Purpose |
|--------|---------|
| [EIP-712](https://eips.ethereum.org/EIPS/eip-712) domain separator | Binds signature to specific chain + contract |
| Nonces | Prevents reuse (increment or mark consumed) |
| Expiry timestamps | Time-limits signature validity |
| [EIP-155](https://eips.ethereum.org/EIPS/eip-155) | Chain ID in transaction signatures |

**Bottom line:** Always bind signatures to **who** (contract address), **where** (chain ID), and **when** (nonce/expiry) they can be used.

---

## Why shouldn't upgradeable contracts use constructors?

**The problem:** In proxy patterns ([Transparent](https://docs.openzeppelin.com/contracts/4.x/api/proxy#TransparentUpgradeableProxy), [UUPS](https://docs.openzeppelin.com/contracts/4.x/api/proxy#UUPSUpgradeable)), the **proxy holds storage** while the implementation provides logic. Constructors run during implementation deployment and set state on the implementation contract, **not the proxy**, making that state inaccessible.

**The solution:** Use `initialize()` functions instead:

```solidity
// ❌ Wrong - State lost on proxy
contract MyTokenV1 {
    address public owner;
    
    constructor() {
        owner = msg.sender;  // Sets owner on implementation, not proxy!
    }
}

// ✅ Correct - State set on proxy
contract MyTokenV1 is Initializable {
    address public owner;
    
    function initialize() public initializer {
        owner = msg.sender;  // Sets owner on proxy storage
    }
}
```

**Key points:**
- Use [OpenZeppelin's `Initializable`](https://docs.openzeppelin.com/contracts/4.x/api/proxy#Initializable) base contract
- `initializer` modifier ensures function runs only once (like a constructor)
- Call `initialize()` via proxy after deployment

**Best Practice:** Always use initializers for upgradeable contracts; reserve constructors for immutable contracts only.

---

## What's the difference between `CREATE` and `CREATE2`?

Both opcodes deploy contracts, but they calculate addresses differently. **CREATE2** enables **deterministic address generation**.

**Address Calculation:**

| Opcode | Formula | Deterministic? |
|--------|---------|----------------|
| **`CREATE`** | `keccak256(rlp([sender, nonce]))` | ❌ Depends on nonce |
| **`CREATE2`** | `keccak256(0xff, sender, salt, keccak256(initCode))` | ✅ Fully deterministic |

**Key difference:** With **CREATE2**, you can calculate the contract address **before deployment** and it remains the same across chains with identical salt and bytecode.

**Why CREATE2 matters:**

1. **Counterfactual deployment**: Interact with an address before deploying the contract
2. **Cross-chain consistency**: Same address on multiple chains (Ethereum, Polygon, etc.)
3. **Factory patterns**: Predict contract addresses in advance
4. **Account abstraction**: Deploy smart wallets at deterministic addresses

**Example:**

```solidity
// CREATE - address depends on nonce (unpredictable)
function deployWithCreate(bytes memory bytecode) public returns (address) {
    address addr;
    assembly {
        addr := create(0, add(bytecode, 0x20), mload(bytecode))
    }
    return addr; // Different each time, depends on deployer nonce
}

// CREATE2 - address is deterministic
function deployWithCreate2(bytes memory bytecode, bytes32 salt) 
    public returns (address) 
{
    address addr;
    assembly {
        addr := create2(0, add(bytecode, 0x20), mload(bytecode), salt)
    }
    return addr; // Same address given same salt & bytecode
}

// Compute CREATE2 address off-chain
function computeCreate2Address(
    bytes32 salt,
    bytes32 bytecodeHash,
    address deployer
) public pure returns (address) {
    return address(uint160(uint256(keccak256(abi.encodePacked(
        bytes1(0xff),
        deployer,
        salt,
        bytecodeHash
    )))));
}
```

**Common use:** Uniswap V2 uses CREATE2 to generate deterministic pair addresses. Introduced in [EIP-1014](https://eips.ethereum.org/EIPS/eip-1014).

---

## What are precompiled contracts?

**Precompiled contracts** are special contracts implemented at the EVM protocol level at fixed addresses (0x01-0x0a). They provide cryptographic and computational operations that would be too expensive to implement in Solidity.

**Why they exist:** Native implementation is orders of magnitude cheaper and faster than EVM bytecode.

**Available Precompiles:**

| Address | Name | Purpose | Added |
|---------|------|---------|-------|
| `0x01` | **ecRecover** | Recover address from signature | Genesis |
| `0x02` | **SHA2-256** | SHA-256 hash function | Genesis |
| `0x03` | **RIPEMD-160** | RIPEMD-160 hash function | Genesis |
| `0x04` | **Identity** | Data copy (returns input) | Genesis |
| `0x05` | **ModExp** | Modular exponentiation | [EIP-198](https://eips.ethereum.org/EIPS/eip-198) |
| `0x06` | **ecAdd** | Elliptic curve addition (alt_bn128) | [EIP-196](https://eips.ethereum.org/EIPS/eip-196) |
| `0x07` | **ecMul** | Elliptic curve multiplication (alt_bn128) | [EIP-196](https://eips.ethereum.org/EIPS/eip-196) |
| `0x08` | **ecPairing** | Elliptic curve pairing check (alt_bn128) | [EIP-197](https://eips.ethereum.org/EIPS/eip-197) |
| `0x09` | **Blake2f** | Blake2 compression function | [EIP-152](https://eips.ethereum.org/EIPS/eip-152) |
| `0x0a` | **Point Evaluation (KZG)** | KZG commitment verification | [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844) |

**Common use cases:**
- **0x01 (ecRecover)**: Signature verification for EIP-712, permits, meta-transactions
- **0x06-0x08**: Zero-knowledge proofs (zkSNARKs)
- **0x0a (KZG)**: Proto-danksharding blob verification

**Example usage:**

```solidity
// ecRecover precompile
function recoverSigner(bytes32 hash, bytes memory signature) 
    public pure returns (address) 
{
    // Calls precompile at 0x01
    return ecrecover(hash, v, r, s);
}

// Manual call to precompile
address precompile = address(0x01);
(bool success, bytes memory result) = precompile.staticcall(data);
```

**Key point:** Precompiles use fixed addresses and can't be upgraded without a hard fork.

---

# Hard

## What is `unchecked` and how is it useful?

`unchecked` is a block that **disables automatic overflow/underflow checks** introduced in Solidity 0.8.0, saving gas when you're certain operations won't overflow.

**Why it exists:** Since Solidity 0.8.0, all arithmetic operations check for overflow/underflow by default. This safety costs gas, which can be avoided when overflow is impossible.

**Gas savings:** ~20-40 gas per operation

**Example:**

```solidity
function demonstrateUnchecked(uint256 iterations) public pure {
    uint256 sum = 0;
    
    // ❌ With checks - more expensive
    for (uint256 i = 0; i < iterations; i++) {
        sum += i;  // Overflow check on every iteration
    }
    
    // ✅ Without checks - cheaper (safe because i++ won't overflow in practice)
    for (uint256 i = 0; i < iterations;) {
        sum += i;
        unchecked { i++; }  // Skip overflow check
    }
    
    // ✅ Entire block unchecked
    unchecked {
        uint256 result = a - b;  // No underflow check
        result *= 2;             // No overflow check
        return result;
    }
}
```

**Common safe use cases:**

| Operation | Why Safe |
|-----------|----------|
| Loop counters (`i++`) | Won't exceed `type(uint256).max` in practice |
| Increments you control | Known bounds prevent overflow |
| After explicit checks | `require(a >= b); unchecked { a - b; }` |

**When NOT to use:**
- User-supplied arithmetic
- Token amounts or balances
- Any calculation where overflow/underflow could be exploited

**Best Practice:** Only use `unchecked` when you can **prove** overflow is impossible. The gas savings aren't worth the security risk in most cases.

---

## What is Yul?

**Yul** is Solidity's low-level intermediate language for writing inline assembly. It provides direct EVM opcode access for **gas optimization** and operations not possible in high-level Solidity.

**Example:**

```solidity
contract YulExample {
    // High-level Solidity
    function addNormal(uint a, uint b) public pure returns (uint) {
        return a + b;
    }
    
    // Yul assembly
    function addYul(uint a, uint b) public pure returns (uint result) {
        assembly {
            result := add(a, b)  // Direct ADD opcode
        }
    }
    
    // Complex example - efficient memory copy
    function memcopy(bytes memory data) public pure returns (bytes memory) {
        bytes memory copy;
        assembly {
            let len := mload(data)
            copy := mload(0x40)  // Free memory pointer
            mstore(0x40, add(copy, add(32, len)))  // Update pointer
            mstore(copy, len)    // Store length
            
            // Copy data (32 bytes at a time)
            let src := add(data, 32)
            let dst := add(copy, 32)
            for { let i := 0 } lt(i, len) { i := add(i, 32) } {
                mstore(add(dst, i), mload(add(src, i)))
            }
        }
        return copy;
    }
}
```

**Common use cases:**
- Gas-critical operations
- Direct memory/storage manipulation
- Custom cryptography
- Proxy implementation logic

**Caution:** No safety checks—you can corrupt memory and state. Use only when necessary!

---

## What is the difference between a cold read and a warm read?

Since the London hard fork ([EIP-2929](https://eips.ethereum.org/EIPS/eip-2929)), storage access costs vary based on whether a slot has been accessed before in the current transaction:

| Access Type | Cost | Description |
|-------------|------|-------------|
| **Cold Read** | 2100 gas | First access to a storage slot or contract address |
| **Warm Read** | 100 gas | Subsequent access to the same slot/address |

**How it works:** The EVM tracks accessed slots in transaction state. Once accessed, they're marked "warm" for the rest of the transaction.

**Gas optimization:** Cache storage values in memory to avoid multiple SLOAD operations:

```solidity
// ❌ Bad - 3 cold reads (6300 gas)
function badSum() public view returns (uint) {
    return value + value + value;  // Reads storage 3 times
}

// ✅ Good - 1 cold + 2 memory reads (2100 gas)
function goodSum() public view returns (uint) {
    uint cached = value;  // 1 SLOAD
    return cached + cached + cached;  // Memory access only
}
```

**Applies to:** Storage slots (SLOAD/SSTORE) and external contract calls (same address)

---

## How do you send Ether to a contract that does not have `payable` functions, nor a `receive` or `fallback`?

**The only way: `SELFDESTRUCT` opcode** (also known as `selfdestruct()`)

When a contract self-destructs, it **forcefully sends all its Ether** to a target address, bypassing all payability checks:

```solidity
contract Forcer {
    function forceEther(address target) external payable {
        selfdestruct(payable(target));
    }
}

contract NoReceiver {
    // No payable functions, no receive, no fallback
    // Still receives ETH via selfdestruct!
}
```

**Why it works:**

`selfdestruct()` operates at the **protocol level**, not the contract level. The Ether transfer happens during transaction finalization, completely bypassing the target contract's code execution.

**Why other methods fail:**

- `.transfer()` / `.send()` → Revert (requires payable receiver)
- `.call{value: }()` → Revert (requires payable receiver or receive/fallback)
- Regular transactions → Revert (no payable entry point)

**Important note:**

`selfdestruct` is **deprecated** as of [EIP-6049](https://eips.ethereum.org/EIPS/eip-6049) and may be removed or restricted in future Ethereum upgrades. In some networks/versions, it may only send Ether without actually destroying the contract.

**Security implication:** Contracts should **never** assume their balance equals tracked deposits, as forced Ether transfers can break balance-dependent logic.

---

## What is Account Abstraction, and what patterns can be used to implement it?

**Account Abstraction (AA)** allows smart contracts to act as user accounts, enabling features like gasless transactions, social recovery, multi-sig wallets, and custom validation logic—making EOAs programmable.

**Evolution of Account Abstraction:**

**1. Meta-Transactions (EIP-712) - Early Pattern:**

Users sign [EIP-712](https://eips.ethereum.org/EIPS/eip-712) typed data off-chain, and a relayer submits it on-chain, paying gas:

```solidity
contract Forwarder {
    function execute(
        address from,
        address to,
        bytes calldata data,
        bytes calldata signature
    ) external {
        bytes32 hash = keccak256(abi.encode(from, to, data, nonce[from]++));
        address signer = ECDSA.recover(hash, signature);
        require(signer == from, "Invalid signature");
        
        (bool success, ) = to.call(data);
        require(success);
    }
}
```

**Limitations:** Not true AA, requires per-contract integration, no standardization.

**2. ERC-4337 (Current Standard):**

[ERC-4337](https://eips.ethereum.org/EIPS/eip-4337) introduces **UserOperations** processed by **Bundlers** through an **EntryPoint** contract, achieving AA without protocol changes:

**Architecture:**
```
User → UserOp (signed) → Bundler → EntryPoint → Smart Wallet
                                         ↓
                                    Paymaster (optional)
```

**Key components:**

| Component | Purpose |
|-----------|---------|
| **UserOperation** | Transaction-like object with custom validation |
| **Smart Wallet** | Contract implementing `IAccount` interface |
| **EntryPoint** | Singleton contract handling UserOps |
| **Bundler** | Off-chain service submitting UserOps on-chain |
| **Paymaster** | Optional contract sponsoring gas fees |

**Example UserOp:**

```solidity
struct UserOperation {
    address sender;           // Smart wallet address
    uint256 nonce;
    bytes initCode;          // Wallet deployment code (if needed)
    bytes callData;          // Actual transaction
    uint256 callGasLimit;
    uint256 verificationGasLimit;
    uint256 preVerificationGas;
    uint256 maxFeePerGas;
    uint256 maxPriorityFeePerGas;
    bytes paymasterAndData;  // Paymaster address + data
    bytes signature;         // Wallet validates this
}
```

**Features:**
- Gasless transactions (Paymaster pays)
- Social recovery
- Session keys
- Batched operations
- Custom validation logic (e.g., WebAuthn, multi-sig)

**3. EIP-7702 (Latest - Pectra Upgrade):**

[EIP-7702](https://eips.ethereum.org/EIPS/eip-7702) allows **EOAs to temporarily delegate to contract code** for the duration of a transaction:

**How it works:**

```solidity
// User signs authorization to delegate to a contract
Authorization {
    chainId: 1,
    address: delegateContract,  // Contract to delegate to
    nonce: 0
}

// During transaction, EOA behaves like delegateContract
// After transaction, EOA returns to normal
```

**Key differences from ERC-4337:**

| Feature | ERC-4337 | EIP-7702 |
|---------|----------|----------|
| **Protocol changes** | None | Protocol-level |
| **Account type** | Smart contract | EOA (temporarily) |
| **Persistence** | Permanent | Per-transaction |
| **Compatibility** | New wallets only | Works with existing EOAs |

**Advantages:**
- Existing EOAs get AA features instantly
- No need to migrate funds
- Simpler onboarding
- Lower gas (no separate wallet deployment)

**Example use:**
```
Alice (EOA) → Signs EIP-7702 auth → Delegates to MultisigLogic
     ↓
Transaction runs with multisig validation
     ↓
After tx, Alice is normal EOA again
```

**Comparison:**

| Pattern | Pros | Cons |
|---------|------|------|
| **EIP-712 Meta-tx** | Simple, no new contracts | No standardization, limited features |
| **ERC-4337** | Full AA, no protocol changes | Complex, requires new infrastructure |
| **EIP-7702** | Native, works with EOAs | Requires hard fork, per-transaction only |

**Best Practice:** Use ERC-4337 for new smart wallets, EIP-7702 for enabling AA on existing EOAs (once widely supported).

---

## What is a Diamond Pattern?

The **Diamond Pattern** ([EIP-2535](https://eips.ethereum.org/EIPS/eip-2535)) is an advanced proxy pattern that allows a single contract to use **multiple implementation contracts** (facets) simultaneously, overcoming the 24KB contract size limit.

**Key innovation:** Unlike standard proxies (one implementation), diamonds route function calls to different facets based on function selectors.

**Architecture:**

```
        Diamond Proxy
             |
    ┌────────┼────────┐
    ↓        ↓        ↓
 Facet A  Facet B  Facet C
(funcs    (funcs   (funcs
 1-10)     11-20)   21-30)
```

**Core components:**

| Component | Purpose |
|-----------|---------|
| **Diamond** | Main proxy contract, holds state |
| **Facets** | Implementation contracts with logic |
| **DiamondCut** | Manages adding/replacing/removing facets |
| **Loupe** | Query which facets/functions are available |

**Benefits:**
- **Unlimited size**: Split logic across multiple contracts
- **Modular upgrades**: Upgrade individual facets without touching others
- **Shared state**: All facets operate on same storage
- **Gas efficient**: Only loads needed facets

**Example:**

```solidity
// Diamond delegates based on function selector
contract Diamond {
    mapping(bytes4 => address) selectorToFacet;
    
    fallback() external payable {
        address facet = selectorToFacet[msg.sig];
        require(facet != address(0), "Function not found");
        
        assembly {
            calldatacopy(0, 0, calldatasize())
            let result := delegatecall(gas(), facet, 0, calldatasize(), 0, 0)
            returndatacopy(0, 0, returndatasize())
            switch result
            case 0 { revert(0, returndatasize()) }
            default { return(0, returndatasize()) }
        }
    }
}
```

**Use cases:** Large dApps (Aavegotchi, DeFi protocols), complex systems needing modular upgrades

**Best Practice:** Use [OpenZeppelin's Diamond implementation](https://github.com/mudgen/diamond) or similar libraries for standard compliance.

---

## Describe the three types of storage gas costs for writes

Storage write costs vary based on the type of operation:

| Operation | Description | Gas Cost (Warm) | Notes |
|-----------|-------------|-----------------|-------|
| **Zero → Non-Zero** | Create new slot | ~20,000 | Most expensive (adds state) |
| **Non-Zero → Zero** | Clear slot | ~5,000 | Gives 15,000 gas refund* |
| **Non-Zero → Non-Zero** | Update slot | ~5,000 | Moderate cost |

*Refunds capped at 20% of transaction gas ([EIP-3529](https://eips.ethereum.org/EIPS/eip-3529))

**Additional factors:**

- **Cold slots** ([EIP-2929](https://eips.ethereum.org/EIPS/eip-2929)): First access costs +2,100 gas
- **Multiple writes**: Subsequent writes to same slot ~100 gas
- **Reverting to original**: May get partial refund if you change back in same transaction

**Optimization tips:**

```solidity
// ❌ Expensive - Creates new slot
uint256 public counter = 0;

// ✅ Better - Avoid unnecessary initialization (default is 0)
uint256 public counter;

// ✅ Gas refund - Delete when done
delete largeMapping[key];  // Frees storage
```

**Key takeaway:** Creating state is expensive, clearing it gives refunds, updating is moderate.

---

## What is a storage collision in a proxy contract?

A **storage collision** occurs when a proxy contract and its implementation contract use the same storage slots for different variables, causing **data corruption**.

**Why it happens:**

With `delegatecall`, the implementation contract's code runs in the **proxy's storage context**. If both define variables starting at slot 0, they overwrite each other.

**Example collision:**

```solidity
// Proxy contract
contract Proxy {
    address public implementation; // slot 0
    address public admin;          // slot 1
}

// Implementation contract  
contract Implementation {
    uint256 public value;  // slot 0 - COLLISION with implementation!
    uint256 public count;  // slot 1 - COLLISION with admin!
}
```

**Solutions:**

**1. [EIP-1967](https://eips.ethereum.org/EIPS/eip-1967) - Standard proxy storage slots:**

Uses pseudo-random, hardcoded slots for proxy metadata:
```solidity
// Slot: keccak256("eip1967.proxy.implementation") - 1
bytes32 private constant IMPLEMENTATION_SLOT = 0x360894a13ba1a3210667c828492db98dca3e2076cc3735a920a3ca505d382bbc;
```

**2. Storage gaps:**

Reserve slots for future variables in base contracts:
```solidity
contract MyUpgradeable {
    uint256 public value;
    uint256[49] private __gap; // Reserve 49 slots
}
```

**Best Practice:** Use [OpenZeppelin's upgradeable contracts](https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable) which implement EIP-1967 and storage gaps automatically.

---

## What is the difference between `transfer` and `send`? Why should they not be used?

**Key Differences:**

| Method | Gas Limit | On Failure | Return Value |
|--------|-----------|------------|--------------|
| `.transfer()` | 2300 gas | Reverts | None |
| `.send()` | 2300 gas | Returns `false` | `bool` |
| `.call{value: }()` | All remaining gas | Returns `false` | `(bool, bytes)` |

**Why avoid `.transfer()` and `.send()`:**

1. **Fixed 2300 gas** is no longer safe after [EIP-1884](https://eips.ethereum.org/EIPS/eip-1884) increased SLOAD costs
2. May fail for legitimate receivers (smart wallets, multisigs with logging)
3. No flexibility for custom receiver logic

**Modern best practice:**

```solidity
// ❌ Deprecated
recipient.transfer(amount);

// ❌ Deprecated  
require(recipient.send(amount), "Send failed");

// ✅ Recommended
(bool success, ) = recipient.call{value: amount}("");
require(success, "Transfer failed");
```

**Bottom line:** Use `.call{value: }("")` with proper checks. It forwards all gas and is forward-compatible with gas cost changes.

---

## What is the free memory pointer and where is it stored?

The **free memory pointer** tracks the next available memory location in the EVM. Since memory grows dynamically, Solidity uses this pointer to prevent overwriting existing data.

**Location & Value:**

| Property | Value | Description |
|----------|-------|-------------|
| **Stored at** | `0x40` | Memory slot holding the pointer |
| **Initial value** | `0x80` (128 bytes) | First 64 bytes reserved for scratch space and hash functions |
| **Updates** | After each allocation | Pointer moves to next free slot |

**How it works:**

1. Solidity reads the pointer at `0x40` to find free memory
2. Writes new data (e.g., `abi.encode`, arrays, strings) starting at that location
3. Updates the pointer at `0x40` to point after the written data

**Example in assembly:**

```solidity
function allocateMemory(uint256 size) internal pure returns (bytes memory) {
    bytes memory result;
    assembly {
        // Read free memory pointer
        let ptr := mload(0x40)
        
        // Allocate memory
        result := ptr
        
        // Update free memory pointer (ptr + size)
        mstore(0x40, add(ptr, size))
    }
    return result;
}
```

**Why it matters:** Understanding this is crucial for optimizing inline assembly code and avoiding memory corruption.