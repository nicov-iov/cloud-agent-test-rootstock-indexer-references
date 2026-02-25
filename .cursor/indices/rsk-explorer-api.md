# LLM Index - rsk-explorer-api

> Reference index for agents. Use this document to quickly navigate the rsk-explorer-api package.

## Project Overview

**rsk-explorer-api** is the REST/WebSocket API and block indexer for the RSK Explorer. It syncs blocks from an RSK node, indexes them into PostgreSQL, and exposes them via HTTP and WebSocket.

- **Stack**: Node.js, Babel, Express, Socket.io, Prisma, PostgreSQL
- **Version**: 2.4.0
- **Repo**: https://github.com/rsksmart/rsk-explorer-api

---

## Project Structure

```
rsk-explorer-api/
├── src/
│   ├── api/                    # HTTP/WS API server
│   │   ├── index.js            # API entry point
│   │   ├── Api.js              # Main API class, module registry
│   │   ├── modules/            # blocks, tx, address, event, token, etc.
│   │   └── api.pm2.config.js
│   ├── services/               # Block indexing
│   │   ├── index.js            # Blocks service entry
│   │   ├── liveSyncer.js       # Live block sync
│   │   ├── staticSyncer.js     # Backfill missing blocks
│   │   ├── txPool.js           # Tx pool service
│   │   └── blocks.pm2.config.js
│   ├── lib/                    # defaultConfig.js, config.js, prismaClient
│   ├── repositories/          # Prisma DB access
│   └── tools/                  # CLI tools
├── prisma/schema.prisma        # PostgreSQL schema
├── doc/api.md                  # API documentation
├── config-example.json
├── Dockerfile
└── docker-compose.yml
```

---

## Entry Points

| Entry | Path | Purpose |
|-------|------|---------|
| **API** | `src/api/index.js` | HTTP + WebSocket server (port 3003) |
| **Blocks** | `src/services/index.js` | Block indexing (liveSyncer, staticSyncer, txPool) |

---

## API Modules

| Module | Purpose |
|--------|---------|
| Blocks | getBlock, getBlocks |
| Tx | getTx, getTxs |
| Address | Address operations |
| Event | Event logs |
| Token | Token balances |
| ContractVerification | Contract verification (rsk-contract-verifier) |
| Stats, Summary, Balances, Contract, InternalTx | Various |

---

## Services

- **liveSyncer**: Syncs new blocks from chain tip (~3s)
- **staticSyncer**: Backfills missing blocks (every 2h)
- **txPool**: Syncs pending/queued transactions

---

## Configuration

- **defaultConfig.js**: `src/lib/defaultConfig.js` – source, db, api, blocks
- **Override**: `config.json` at project root (see config-example.json)
- **Contract verifier**: `api.contractVerifier.url` (WebSocket to rsk-contract-verifier)

---

## Commands

| Command | Description |
|---------|-------------|
| `npm run build` | Babel + api-docs |
| `npm run start-blocks` | Indexador |
| `npm run start-api` | Servidor API |
| `npm run dev` | Desarrollo |
| `npx prisma generate` | Cliente Prisma |

---

## Quick Find

| Need | Path |
|------|------|
| Add API module | `src/api/modules/` |
| DB schema | `prisma/schema.prisma` |
| Config defaults | `src/lib/defaultConfig.js` |
| Block indexing | `src/services/classes/Block.js` |
| API docs | `doc/api.md`, `public/swagger.json` |
