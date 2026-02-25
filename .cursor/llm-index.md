# LLM Index - RSK Blockchain Tools Monorepo

> Índice de referencia para agentes. Usa este documento para navegar el repositorio. Para análisis profundo de un proyecto, delega a un subagente (mcp_task) con el path correspondiente y consulta el índice específico.

## Resumen del Proyecto

Monorepo de herramientas **Rootstock (RSK)** - blockchain sidechain de Bitcoin. Stack: JavaScript/TypeScript, Node.js ≥16 (≥20 para rsk-contract-parser).

## Estructura de Paquetes

```
workspace/
├── nod3/                    # Cliente RPC base (Ethereum/RSK)
├── rsk-utils/               # Utilidades JS (checksums, redes)
├── rsk-js-cli/              # Librería CLI
├── rsk-contract-parser/     # Parser de contratos y eventos
└── rsk-explorer-api/        # API REST/WS e indexador de bloques
```

## Índices por Sub-referencia

Cada proyecto tiene su propio índice. **Para análisis de un proyecto, usa mcp_task con subagent_type explorar/generalPurpose y el path del proyecto.**

| Proyecto | Índice | Path | Delegar a subagente para |
|----------|--------|------|--------------------------|
| **nod3** | [.cursor/indices/nod3.md](.cursor/indices/nod3.md) | `nod3/` | RPC, eth/net/web3/txpool/debug/trace |
| **rsk-utils** | [.cursor/indices/rsk-utils.md](.cursor/indices/rsk-utils.md) | `rsk-utils/` | Checksums, direcciones, EIP-1191 |
| **rsk-js-cli** | [.cursor/indices/rsk-js-cli.md](.cursor/indices/rsk-js-cli.md) | `rsk-js-cli/` | CLI, argumentos, logging |
| **rsk-contract-parser** | [.cursor/indices/rsk-contract-parser.md](.cursor/indices/rsk-contract-parser.md) | `rsk-contract-parser/` | Contratos, eventos, ABIs, Bridge, Remasc |
| **rsk-explorer-api** | [.cursor/indices/rsk-explorer-api.md](.cursor/indices/rsk-explorer-api.md) | `rsk-explorer-api/` | API, indexación, PostgreSQL, config |
| **rsk-contract-verifier** | [.cursor/indices/rsk-contract-verifier.md](.cursor/indices/rsk-contract-verifier.md) | (externo) | Verificación contratos |
| **rskj** | [.cursor/indices/rskj.md](.cursor/indices/rskj.md) | (externo) | Nodo RSK, configuración |

## Flujo de Dependencias

```
nod3 (base RPC)
    ↓
rsk-utils ← rsk-contract-parser
    ↓           ↓
rsk-js-cli ← rsk-explorer-api
```

## Delegación a Subagentes

Para alivianar la carga del agente principal, **delega a subagentes** cuando el análisis sea específico de un proyecto:

```text
mcp_task: subagent_type=explore o generalPurpose
prompt: "Analiza [path] según [.cursor/indices/[proyecto].md]. Tarea: ..."
```

Ejemplo: análisis de nod3 → `mcp_task` con path `nod3/` y referencia al índice de nod3.

## Ubicaciones Clave (globales)

- **Config**: `rsk-explorer-api/src/lib/defaultConfig.js`, `config-example.json`
- **DB**: `rsk-explorer-api/prisma/schema.prisma`
- **API docs**: `rsk-explorer-api/doc/api.md`, `rsk-explorer-api/public/swagger.json`
- **Docker**: `rsk-explorer-api/Dockerfile`, `dockerized/`

## Comandos Útiles

```bash
cd <package> && npm run build
cd <package> && npm test
```

## Licencia

MIT para todos los paquetes.
