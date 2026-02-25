# rsk-js-cli — LLM Index

> Quick reference for agents working with @rsksmart/rsk-js-cli

## Overview

| Property | Value |
|----------|-------|
| **Package** | `@rsksmart/rsk-js-cli` |
| **Version** | 1.0.0 |
| **Purpose** | Simple library to write Node.js CLI tools |
| **Repo** | https://github.com/rsksmart/rsk-js-cli |
| **Path** | `rsk-js-cli/` |

## Project Structure

```
rsk-js-cli/
├── cli.js              # Entry point & sole source file
├── package.json
└── README.md
```

## Main Exports (cli.js)

| Export | Description |
|--------|--------------|
| `reset`, `red`, `blue`, `green`, `orange`, `yellow`, `grey` | ANSI color codes |
| `ok`, `example`, `label` | Colored output helpers |
| `log` | Proxy: `log.error`, `log.warn`, `log.info`, `log.debug` |
| `write`, `writeLine` | Raw stdout output |
| `progressBar` | Progress bar string |
| `parseArg`, `getArgs` | CLI argument parsing |
| `icons` | square, circle, ok, check, error, etc. |

## Usage in Monorepo

**Consumed by:** `rsk-explorer-api` (tools: wsGet, wsChannel, statusClient, getBlock)

## Commands

| Command | Description |
|---------|-------------|
| `npm run lint` | ESLint on *.js |
