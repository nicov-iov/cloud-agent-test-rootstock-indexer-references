# rsk-contract-parser — LLM Index

> NodeJS module to parse, analyze, and interact with smart contracts and native RSK contracts on the Rootstock blockchain.

## Quick Reference

| Item | Location |
|------|----------|
| **Entry point** | `src/index.js` → built to `dist/index.js` |
| **Main class** | `src/lib/ContractParser.js` |
| **Contract interaction** | `src/lib/Contract.js` |
| **Blockchain search** | `src/lib/BcSearch.js` |
| **Node provider** | `src/lib/nod3Connect.js` → `createRskNodeProvider` |
| **Native contracts** | `src/lib/nativeContracts/` |
| **JSON ABIs** | `src/lib/jsonAbis/` |
| **Compiled default ABI** | `src/lib/compiled_abi.json` (from `npm run abi`) |

---

## Project Structure

```
rsk-contract-parser/
├── src/
│   ├── index.js                 # Main entry, exports
│   ├── lib/
│   │   ├── ContractParser.js     # Main parser class
│   │   ├── Contract.js          # Contract interaction (call, encode/decode)
│   │   ├── BcSearch.js           # Blockchain search (deploymentBlock, deploymentTx)
│   │   ├── EventDecoder.js      # Decode logs via @ethersproject/abi
│   │   ├── Abi.js               # Default ABI
│   │   ├── nod3Connect.js      # createRskNodeProvider, publicRskNodeUrls
│   │   ├── nativeContracts/     # Bridge, Remasc, bridge-*.json
│   │   └── jsonAbis/            # ERC20, ERC721, etc.
├── test/
├── package.json
└── README.md
```

---

## Main Exports

| Export | Description |
|--------|-------------|
| `ContractParser` | Parse contracts, decode events, detect proxies |
| `Contract` | call(), encodeCall(), decodeCall() |
| `BcSearch` | deploymentBlock(), deploymentTx() |
| `createRskNodeProvider` | Create Nod3 for mainnet/testnet |
| `getRskReleaseByBlockNumber` | Bridge ABI for block/network |
| `getLatestBridgeAbi`, `getLatestBridgeMethods` | Latest Bridge |
| `RSK_RELEASES` | Release heights and ABIs per network |

---

## Native Contracts

| Contract | Address | Purpose |
|----------|---------|---------|
| **Bridge** | `0x...1000006` | BTC–RSK bridge |
| **Remasc** | `0x...1000008` | Mining rewards |

Bridge ABIs per RSK release in `bridgeAbi.js` (orchid → reed).

---

## Build & Test Commands

| Command | Description |
|---------|-------------|
| `npm run build` | Lint + Babel src → dist |
| `npm test` | Mocha (excludes BcSearch.spec.js) |
| `npm run abi` | Rebuild compiled_abi.json |

---

## Dependencies

- nod3, @rsksmart/rsk-precompiled-abis, rsk-utils, @ethersproject/abi, bs58, secp256k1
