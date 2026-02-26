# rskj — LLM Index (external repo)

> Reference for the RSK node (Java). External repo: https://github.com/rsksmart/rskj

## Usage in the monorepo

- **nod3**: RPC client to communicate with rskj
- **rsk-explorer-api**: Requires rskj node >= 2.0.1
- **Docker**: PPA `ppa:rsksmart/rskj` in `rsk-explorer-api/dockerized/rsk-node/Dockerfile`
- **nod3 CI**: `.circleci/config.yml` clones and compiles rskj for tests

## Required RPC modules

For explorer-api: eth, net, web3, txpool, debug, trace

## Known workarounds

- **txpool**: rskj issues #689 – incorrect responses
- See: `nod3/src/modules/txpool.js`, `rsk-explorer-api/src/services/classes/TxPool.js`

## Related files

- `nod3/.rskj-conf/node.conf` – config for CI
- `rsk-explorer-api/dockerized/rsk-node/Dockerfile` – Docker image

## Note

rskj is the node that monorepo packages consume via RPC.
