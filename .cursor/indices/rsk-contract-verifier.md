# rsk-contract-verifier — LLM Index (external repo)

> Reference for the contract verification service. External repo: https://github.com/rsksmart/rsk-contract-verifier

## Usage in the monorepo

Integrated as an optional module in **rsk-explorer-api**.

### Enabling

1. Set `api.allowUserEvents = true` in config
2. Configure verifier URL:

```javascript
api: {
  contractVerifier: {
    url: 'ws://localhost:3008'  // WebSocket
  }
}
```

### Related files

- `rsk-explorer-api/src/lib/defaultConfig.js` – base config
- `rsk-explorer-api/README.md` – setup instructions
- API modules: ContractVerification, VerificationResults

## Note

This repo is NOT in the monorepo. For changes to the verifier, work in the external repo.
