# rskj — LLM Index (repo externo)

> Referencia para el nodo RSK (Java). Repo externo: https://github.com/rsksmart/rskj

## Uso en el monorepo

- **nod3**: Cliente RPC para comunicarse con rskj
- **rsk-explorer-api**: Requiere nodo rskj >= 2.0.1
- **Docker**: PPA `ppa:rsksmart/rskj` en `rsk-explorer-api/dockerized/rsk-node/Dockerfile`
- **CI nod3**: `.circleci/config.yml` clona y compila rskj para tests

## Módulos RPC requeridos

Para explorer-api: eth, net, web3, txpool, debug, trace

## Workarounds conocidos

- **txpool**: rskj issues #689 – respuestas incorrectas
- Ver: `nod3/src/modules/txpool.js`, `rsk-explorer-api/src/services/classes/TxPool.js`

## Archivos relacionados

- `nod3/.rskj-conf/node.conf` – config para CI
- `rsk-explorer-api/dockerized/rsk-node/Dockerfile` – imagen Docker

## Nota

rskj es el nodo que los paquetes del monorepo consumen vía RPC.
