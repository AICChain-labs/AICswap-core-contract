<p align="center">
  <img src="https://aic-assets.aicchain.io/android-chrome-192x192.png" width="120" />
</p>

# AIC Mainnet Smart Contracts

This repository contains the **core smart contracts of the AIC Mainnet**, including the Decentralized Exchange (DEX), token contracts, and Multicall aggregation contract used by the frontend.

All contracts are adapted from battle-tested architectures such as **Uniswap V2**, with modifications for the AIC ecosystem.

---

## 🌐 AIC Blockchain Explorer

🔎 Explorer: https://scan.aicchain.io/

All deployed contracts can be verified and inspected on the official AIC explorer.

---

# 📁 Mainnet Deployed Contracts

---

## 1️⃣ USDI (Stablecoin / BEP20 Token)

**Contract:** `USDI.sol`  
**Decimals:** 18  
**Total Supply:** 100,000,000,000 (100 Billion)

**Contract Address:**  
`0xD359Ebfa22d6caFe8Ff49b9e45859F688243CdAC`

🔗 Explorer:  
https://scan.aicchain.io/address/0xD359Ebfa22d6caFe8Ff49b9e45859F688243CdAC

### Overview
USDI is the primary stable asset within the AIC ecosystem.  
The contract follows the `Ownable` model and supports mint and burn mechanisms.

### Core Features
- Fully ERC20/BEP20 compatible  
- `mint` (owner only)  
- `burn` (token holder)  
- Integrated SafeMath  
- 18 decimals standard  

**Compiler Version:** `pragma solidity 0.5.16;`

---

## 2️⃣ AICswapV2Factory (DEX Factory)

Modified from Uniswap V2 Factory.

### Original (Ethereum Mainnet)  
`0x5C69bEe701ef814a2B6a3EDD4B1652CB9cc5aA6f`

### AIC Mainnet Deployment  
`0xb9b001b11c9365A6f440adccFeCF345aEa724881`

🔗 Explorer:  
https://scan.aicchain.io/address/0xb9b001b11c9365A6f440adccFeCF345aEa724881

### Init Code Hash

Original:  
`96e8ac4277198ff8b6f785478aa9a39f403cb768dd02cbee326c3e7da348845f`

AIC:  
`24d843439afe907396c8c562d5ddb89ab39f9a8284feefd1ff4aa768f50110d3`

### Core Function
- `createPair()` — Creates liquidity pools for token pairs.

**Compiler Version:** `pragma solidity =0.5.16;`

---

## 3️⃣ WAIC9 (Wrapped AIC)

Wrapped native AIC token (equivalent to WETH9).

### Original WETH9  
`0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2`

### AIC WAIC9  
`0x4bdC4C23c0D9bdceefe9AaB8d946DA16b75E03Fb`

🔗 Explorer:  
https://scan.aicchain.io/address/0x4bdC4C23c0D9bdceefe9AaB8d946DA16b75E03Fb

### Core Features
- `deposit()` — Wrap native AIC (1:1)  
- `withdraw()` — Unwrap to native AIC  

**Compiler Version:** `pragma solidity ^0.4.18;`

---

## 4️⃣ AICswapV2Router02 (DEX Router)

Main routing contract for liquidity and swaps.

### Original (Ethereum)  
`0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D`

### AIC Mainnet  
`0x773fa2F87c4831607B57926C9c1E8727252c31B2`

🔗 Explorer:  
https://scan.aicchain.io/address/0x773fa2F87c4831607B57926C9c1E8727252c31B2

### Core Features
- `addLiquidity`  
- `removeLiquidity`  
- `swapExactTokensForTokens`  
- `swapTokensForExactETH`  
- FeeOnTransfer token support  

**Compiler Version:** `pragma solidity =0.6.6;`

---

## 5️⃣ Multicall (Batch Query Contract)

Enables multiple contract calls in a single RPC request.

### Original  
`0x5e227AD1969Ea493B43F840cfF78d08a6fc17796`

### AIC Mainnet  
`0x3E1c72dabc3286CF79b40b945b889d294515d104`

🔗 Explorer:  
https://scan.aicchain.io/address/0x3E1c72dabc3286CF79b40b945b889d294515d104

### Core Features
- `aggregate()` — Batch contract calls  
- `getEthBalance`  
- `block.timestamp`  
- `block.difficulty`  
- `block.gaslimit`  

**Compiler Version:** `pragma solidity >=0.5.0;`

---

# 🛠 Development Recommendations

Since contracts use multiple Solidity versions (`0.4.18` → `0.6.6`),  
use frameworks that support multi-compiler configurations:

- Hardhat  
- Foundry  
- Truffle  

---

# 🔐 Security Notice

These contracts are adapted from audited and battle-tested architectures (Uniswap V2 model).  
Any production upgrade or modification should undergo independent security auditing.

---

# 📜 License

GNU GPLv3 (Inherited from Uniswap V2 architecture where applicable)

---

© AIC Chain
