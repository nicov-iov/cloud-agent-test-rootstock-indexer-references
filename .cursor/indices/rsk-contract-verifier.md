# rsk-contract-verifier — LLM Index (repo externo)

> Referencia para el servicio de verificación de contratos. Repo externo: https://github.com/rsksmart/rsk-contract-verifier

## Uso en el monorepo

Integrado como módulo opcional en **rsk-explorer-api**.

### Habilitación

1. `api.allowUserEvents = true` en config
2. Configurar URL del verifier:

```javascript
api: {
  contractVerifier: {
    url: 'ws://localhost:3008'  // WebSocket
  }
}
```

### Archivos relacionados

- `rsk-explorer-api/src/lib/defaultConfig.js` – config base
- `rsk-explorer-api/README.md` – instrucciones de configuración
- Módulos API: ContractVerification, VerificationResults

## Nota

Este repo NO está en el monorepo. Para cambios en el verifier, trabajar en el repo externo.
