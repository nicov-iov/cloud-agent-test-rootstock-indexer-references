# LLM Index - RSK Blockchain Tools Monorepo

> Índice de referencia para agentes. Usa este documento para navegar rápidamente el repositorio y delegar tareas a los subagentes especializados.

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

## Flujo de Dependencias

```
nod3 (base RPC)
    ↓
rsk-utils ← rsk-contract-parser
    ↓           ↓
rsk-js-cli ← rsk-explorer-api
```

## Referencia Rápida por Paquete

| Paquete | Path | Repo | Entrada | Descripción |
|---------|------|------|---------|-------------|
| **nod3** | `nod3/` | [rsksmart/nod3](https://github.com/rsksmart/nod3) | `dist/index.js` | Cliente RPC mínimo para nodos Ethereum/RSK |
| **rsk-utils** | `rsk-utils/` | [rsksmart/rsk-utils](https://github.com/rsksmart/rsk-utils) | `dist/cjs/index.js` | Checksums EIP-1191, validación de direcciones |
| **rsk-js-cli** | `rsk-js-cli/` | [rsksmart/rsk-js-cli](https://github.com/rsksmart/rsk-js-cli) | `cli.js` | Utilidades para herramientas CLI |
| **rsk-contract-parser** | `rsk-contract-parser/` | [rsksmart/rsk-contract-parser](https://github.com/rsksmart/rsk-contract-parser) | `dist/index.js` | Parseo de contratos, eventos, proxies, Bridge/Remasc |
| **rsk-explorer-api** | `rsk-explorer-api/` | [rsksmart/rsk-explorer-api](https://github.com/rsksmart/rsk-explorer-api) | `index.js` | API REST/WS, indexador de bloques, PostgreSQL |

## Ubicaciones Clave

### Configuración
- **Explorer API**: `rsk-explorer-api/src/lib/defaultConfig.js`, `config-example.json`
- **Base de datos**: `rsk-explorer-api/prisma/schema.prisma`, `rsk-explorer-api/prisma/rsk-explorer-database.sql`
- **API docs**: `rsk-explorer-api/doc/api.md`, `rsk-explorer-api/public/swagger.json`

### Servicios PM2 (rsk-explorer-api)
- API: `dist/api/api.pm2.config.js`
- Blocks: `dist/services/blocks.pm2.config.js`

### Docker
- `rsk-explorer-api/Dockerfile` - API y blocks
- `rsk-explorer-api/dockerized/rsk-node/Dockerfile` - Nodo RSK
- `rsk-explorer-api/dockerized/mongod/Dockerfile` - MongoDB

### Tests
- `nod3/test/`, `rsk-utils/test/`, `rsk-contract-parser/test/`, `rsk-explorer-api/test/`

## Repos Externos Referenciados

| Repo | URL | Uso |
|------|-----|-----|
| **rsk-contract-verifier** | [rsksmart/rsk-contract-verifier](https://github.com/rsksmart/rsk-contract-verifier) | Verificación de contratos (módulo opcional en explorer-api) |
| **rskj** | [rsksmart/rskj](https://github.com/rsksmart/rskj) | Nodo RSK (PPA, CI en nod3) |
| **rsk-precompiled-abis** | npm `@rsksmart/rsk-precompiled-abis` | ABIs de contratos nativos RSK |

## Subagentes Disponibles

Para tareas específicas de cada paquete o repo externo, delega al subagente correspondiente:

| Subagente | Cuándo usar |
|-----------|-------------|
| `nod3` | RPC, comunicación con nodo, txpool, debug, trace |
| `rsk-utils` | Checksums, validación direcciones, utilidades RSK |
| `rsk-js-cli` | Herramientas CLI, argumentos, comandos |
| `rsk-contract-parser` | Contratos, eventos, ABIs, Bridge, Remasc, proxies |
| `rsk-explorer-api` | API REST/WS, indexación, PostgreSQL, bloques |
| `rsk-contract-verifier` | Verificación de contratos Solidity |
| `rskj` | Nodo RSK, configuración, Java |

## Comandos Útiles

```bash
# Build
cd <package> && npm run build

# Tests
cd nod3 && npm test
cd rsk-utils && npm run test
cd rsk-contract-parser && npm test
cd rsk-explorer-api && npm test

# Explorer API
npm run start-blocks   # Indexador
npm run start-api      # Servidor API
npm run dev            # Desarrollo
```

## Licencia

MIT para todos los paquetes.
