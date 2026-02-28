# AIC Mainnet Smart Contracts

This repository contains the core smart contracts for the AIC project, mainly divided into the core components for the Decentralized Exchange (DEX), token contracts, and the Multicall aggregated query contract used by the frontend. All contracts are developed and adapted based on mature solutions.

## 📁 Included Contracts

### 1. `AicswapV2Factory.sol` (Aicswap Factory Contract)
**Overview:** 
This contract is a token pool factory contract modified based on the Uniswap V2 architecture, primarily responsible for creating instances of various trading pairs (Pair) and setting up global fee configurations for the entire DEX system.
**Core Features:**
* **`createPair`**: Creates a new trading pair (liquidity pool) for two different specified ERC20 tokens.

**Compiler Version:** `pragma solidity =0.5.16;`

### 2. `AicswapV2Router02.sol` (Aicswap Router Contract)
**Overview:** 
Responsible for routing control and liquidity management for all trading pairs created within `AicswapV2Factory`. It is the main entry point for end users and DApps to interact with the protocol.
**Core Features:**
* **Provide/Remove Liquidity**: Supports `addLiquidity`, `addLiquidityETH`, `removeLiquidity`, etc.
* **Token Swaps**: Provides precise swapping capabilities, such as `swapExactTokensForTokens`, `swapTokensForExactETH`, and their corresponding variants. It has good compatibility and support for tokens containing "deflationary tax mechanisms (FeeOnTransfer)".
**Compiler Version:** `pragma solidity =0.6.6;`

### 3. `USDI.sol` (USDI Stablecoin/Token)
**Overview:** 
USDI is a standard ERC20/BEP20 compliant token implementation. The contract defaults to the `Ownable` model, granting the owner the ability to mint and manage operations.
**Core Features:**
* **Fully ERC20 Compliant**: Supports main methods such as `transfer`, `approve`, `transferFrom`, etc.
* **`mint` and `burn`**: The contract administrator has the permission to issue additional tokens (`mint`). All token holders can use `burn` to destroy their own tokens to reduce the total supply.
* **Security Features**: Integrates the SafeMath engine internally to avoid integer overflow issues.
**Compiler Version:** `pragma solidity 0.5.16;`

### 4. `WAIC9.sol` (Wrapped AIC)
**Overview:** 
Since the native currency of AIC cannot directly interact with the ERC20 contract standard, the WAIC contract is introduced as an alternative to WETH, used to wrap native AIC at a 1:1 ratio and convert it into a standard ERC20 token.
**Core Features:**
* **`deposit`**: Users send native AIC assets and receive standardized WAIC at a 1:1 ratio. Can also be triggered directly by transferring assets to the contract.
* **`withdraw`**: Destroys WAIC tokens and withdraws native AIC to the original account address.
**Compiler Version:** `pragma solidity ^0.4.18;`

### 5. `Multicall.sol` (Multi-Request Aggregation Contract)
**Overview:** 
This contract enables Decentralized Applications (DApps) to batch call and query the state of multiple smart contracts on the blockchain through a single RPC JSON request, effectively reducing network loading time and communication costs, and improving the responsiveness of the Web3 frontend.
**Core Features:**
* **`aggregate`**: Aggregated query module. Allows DApps to submit a parameter group consisting of multiple addresses and their corresponding encoded `callData`, and sequentially retrieve all results within a single block.
* **Fetch Block Data**: Provides minimalistic interfaces to fetch the current `block.timestamp`, `block.difficulty`, `block.gaslimit`, and raw balance (`getEthBalance`).
**Compiler Version:** `pragma solidity >=0.5.0;`

## 🛠 Development & Deployment Recommendations

### Compilation Environment
Since the contracts above use various Solidity versions ranging from `0.4.18` to `0.6.6`, it is recommended to use development frameworks like Hardhat, Truffle, or Foundry that support Multi-Compiler configurations in independent config files for standardized compilation.
