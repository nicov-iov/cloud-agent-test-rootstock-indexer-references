# LLM Index - nod3 (@rsksmart/nod3)

> Reference index for agents. Use this document to quickly navigate the nod3 RPC client and find what you need.

## Overview

**nod3** is a minimal JavaScript RPC client for Ethereum/RSK nodes. No runtime dependencies. Used by rsk-contract-parser and rsk-explorer-api.

- **Path**: `nod3/`
- **Repo**: https://github.com/rsksmart/nod3
- **Version**: 0.5.0

---

## Project Structure

```
nod3/
├── src/
│   ├── index.js                 # Main entry, exports Nod3, Nod3Hub, Nod3Router
│   ├── classes/
│   │   ├── Nod3.js              # Core client class
│   │   ├── Nod3Hub.js            # Multi-provider round-robin
│   │   ├── Nod3Router.js         # Route methods to specific providers
│   │   ├── Provider.js           # Base provider (abstract)
│   │   ├── HttpProvider.js       # HTTP JSON-RPC provider
│   │   ├── CurlProvider.js       # Curl-based provider (debug)
│   │   ├── HttpClient.js         # HTTP client
│   │   ├── JsonRpc.js            # JSON-RPC payload/send
│   │   ├── Subscribe.js          # Subscriptions (filters, methods)
│   │   └── Subscription.js       # Single subscription
│   ├── modules/                  # RPC method definitions
│   │   ├── index.js              # Aggregates all modules
│   │   ├── eth.js                # eth_* methods
│   │   ├── net.js                # net_* methods
│   │   ├── rsk.js                # eth_getBlocksByNumber (RSK-specific)
│   │   ├── txpool.js             # txpool_* methods
│   │   ├── debug.js              # debug_traceTransaction
│   │   └── trace.js              # trace_transaction, trace_block
│   ├── lib/
│   │   ├── types.js              # NETWORKS, NOD3_MODULE, NOD3_HUB
│   │   ├── utils.js              # toHexStr, toDecimal, isHashOrNumber, RoundRobin
│   │   ├── formatters.js         # blockFormatter, txFormatter, txPoolFormatter
│   │   └── filters.js            # newBlock, pendingTransactions
│   └── cli/
│       └── nod3-cli.js           # CLI entry
├── test/
├── .rskj-conf/node.conf         # rskj config for CI
├── package.json
└── README.md
```

---

## Entry Points

| Entry | Path | Description |
|-------|------|-------------|
| **Main** | `dist/index.js` | Library entry (after build) |
| **CLI** | `dist/cli/nod3-cli.js` | Binary `nod3-cli` |
| **Source** | `src/index.js` | Pre-build entry |

---

## Main Exports

- **Nod3** – Main client
- **Nod3Hub** – Multiple providers with round-robin
- **Nod3Router** – Route methods to specific providers
- **Nod3.providers** – `{ HttpProvider, CurlProvider }`

---

## RPC Modules

| Module | File | Key Methods |
|--------|------|-------------|
| **eth** | `src/modules/eth.js` | getBlock, getTransactionByHash, getTransactionReceipt, getCode, call |
| **net** | `src/modules/net.js` | listening, version, peerCount |
| **rsk** | `src/modules/rsk.js` | getBlocksByNumber |
| **txpool** | `src/modules/txpool.js` | content, inspect, status |
| **debug** | `src/modules/debug.js` | traceTransaction |
| **trace** | `src/modules/trace.js` | transaction, block |

**Note**: `txpool.js` includes fixes for rskj issues (#689).

---

## Build Commands

```bash
cd nod3
npm run build    # babel src -d dist
npm run clean    # rm -rf dist
npm run lint     # eslint src/**/*
npm test         # mocha ./test/**/*.spec.js
```

---

## Quick Reference

| Need | Look at |
|------|---------|
| Add RPC method | `src/modules/<module>.js` |
| Change HTTP behavior | `src/classes/HttpProvider.js`, `HttpClient.js` |
| Multi-node routing | `src/classes/Nod3Router.js`, `Nod3Hub.js` |
| Subscriptions | `src/classes/Subscribe.js`, `src/lib/filters.js` |
| Response formatting | `src/lib/formatters.js` |
