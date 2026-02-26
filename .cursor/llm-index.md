# LLM Index - RSK Blockchain Tools Monorepo

> Reference index for agents. Use this document to navigate the repository. For deep analysis of a project, delegate to a subagent (mcp_task) with the corresponding path and consult the specific index.

## Project Summary

Monorepo of **Rootstock (RSK)** tools - Bitcoin sidechain. Stack: JavaScript/TypeScript, Node.js ≥16 (≥20 for rsk-contract-parser).

## Package Structure

```
workspace/
├── nod3/                    # Base RPC client (Ethereum/RSK)
├── rsk-utils/               # JS utilities (checksums, networks)
├── rsk-js-cli/              # CLI library
├── rsk-contract-parser/     # Contract and event parser
└── rsk-explorer-api/        # REST/WS API and block indexer
```

## Indices by Sub-reference

Each project has its own index. **For project analysis, use mcp_task with subagent_type explore/generalPurpose and the project path.**

| Project | Index | Path | npm | Delegate for |
|---------|-------|------|-----|--------------|
| **nod3** | [nod3.md](.cursor/indexes/nod3.md) | `nod3/` | `@rsksmart/nod3` | RPC, eth/net/web3/txpool/debug/trace |
| **rsk-utils** | [rsk-utils.md](.cursor/indexes/rsk-utils.md) | `rsk-utils/` | `@rsksmart/rsk-utils` | Checksums, addresses, EIP-1191 |
| **rsk-js-cli** | [rsk-js-cli.md](.cursor/indexes/rsk-js-cli.md) | `rsk-js-cli/` | `@rsksmart/rsk-js-cli` | CLI, arguments, logging |
| **rsk-contract-parser** | [rsk-contract-parser.md](.cursor/indexes/rsk-contract-parser.md) | `rsk-contract-parser/` | `@rsksmart/rsk-contract-parser` | Contracts, events, ABIs, Bridge, Remasc |
| **rsk-explorer-api** | [rsk-explorer-api.md](.cursor/indexes/rsk-explorer-api.md) | `rsk-explorer-api/` | — | API, indexing, PostgreSQL, config |
| **rsk-contract-verifier** | [rsk-contract-verifier.md](.cursor/indexes/rsk-contract-verifier.md) | (external) | — | Contract verification |
| **rskj** | [rskj.md](.cursor/indexes/rskj.md) | (external) | — | RSK node, configuration |

## Dependency Flow

```
nod3 (base RPC)
    ↓
rsk-utils ← rsk-contract-parser
    ↓           ↓
rsk-js-cli ← rsk-explorer-api
```

## Delegating to Subagents

To lighten the main agent's load, **delegate to subagents** when analysis is project-specific:

```text
mcp_task: subagent_type=explore or generalPurpose
prompt: "Analyze [path] using [.cursor/indexes/[project].md] as reference. Task: ..."
```

Example: nod3 analysis → `mcp_task` with path `nod3/` and reference to nod3 index.

## Key Locations (global)

- **Config**: `rsk-explorer-api/src/lib/defaultConfig.js`, `config-example.json`
- **DB**: `rsk-explorer-api/prisma/schema.prisma`
- **API docs**: `rsk-explorer-api/doc/api.md`, `rsk-explorer-api/public/swagger.json`
- **Docker**: `rsk-explorer-api/Dockerfile`, `dockerized/`

## Useful Commands

```bash
cd <package> && npm run build
cd <package> && npm test
```

## License

MIT for all packages.
