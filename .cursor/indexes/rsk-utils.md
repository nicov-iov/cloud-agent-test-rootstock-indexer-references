# rsk-utils — LLM Index

> Quick reference for agents. Use this to navigate the rsk-utils package and find what you need.

## Overview

**Package**: `@rsksmart/rsk-utils` (v2.0.5)  
**Purpose**: JavaScript utility functions for Rootstock (RSK) blockchain  
**Repo**: https://github.com/rsksmart/rsk-utils

Supports CommonJS and ESM. TypeScript definitions included. Lightweight, single runtime dependency (`keccak`).

---

## Project Structure

```
rsk-utils/
├── src/                    # TypeScript source
│   ├── index.ts            # Main entry, re-exports all modules
│   ├── addresses.ts        # Address validation, checksums (EIP-1191)
│   ├── arrays.ts           # Array utilities
│   ├── bytes.ts            # Buffer/hex conversion
│   ├── data.ts             # sumDigits, isNullData
│   ├── encoding.ts         # Base64, JSON encode/decode
│   ├── hashes.ts           # keccak256
│   ├── strings.ts          # Hex prefix helpers
│   ├── networks.ts         # Network definitions
│   └── networks.json       # Chain data (RSK Mainnet 30, Testnet 31)
├── dist/cjs/               # CommonJS build
├── dist/esm/               # ESM build
├── test/                   # Mocha specs
└── package.json
```

---

## Main Exports

### Addresses (EIP-1191)
- `toChecksumAddress(address, chainId)` – Checksummed address
- `isValidChecksumAddress(address, chainId)` – Validates checksum
- `isAddress(address)` – 40 hex chars validation
- `zeroAddress()`, `ZERO_ADDRESS`, `isZeroAddress()`

### Strings, Bytes, Hashes
- `isHexString`, `add0x`, `stripHexPrefix`, `isTxOrBlockHash`
- `toBuffer`, `bufferToHex`
- `keccak256`

### Encoding, Arrays, Data
- `atob`, `btoa`, `jsonEncode`, `jsonDecode`
- `arrayIntersection`, `arrayDifference`, `hasValue`, `includesAll`
- `sumDigits`, `isNullData`

---

## Build Commands

| Command | Action |
|---------|--------|
| `npm run build` | Build ESM + CJS |
| `npm run test` | c8 + mocha |
| `npm run lint` | ESLint on src/*.ts |

---

## Quick Find

| Need | Location |
|------|----------|
| Address checksums | `src/addresses.ts` |
| Network definitions | `src/networks.ts`, `src/networks.json` |
| Keccak hash | `src/hashes.ts` |
