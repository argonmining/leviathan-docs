# Testnet constants

Authoritative quick reference for the public Leviathan **testnet** environment. Mainnet values are out of scope.

## Hosted URLs

| Service | URL |
|---------|-----|
| Explorer (home) | [https://leviathandev.neptune.io/](https://leviathandev.neptune.io/) |
| Wallet | [https://leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet) |
| Bridge monitor | [https://leviathandev.neptune.io/bridge](https://leviathandev.neptune.io/bridge) |
| Blocks | [https://leviathandev.neptune.io/blocks](https://leviathandev.neptune.io/blocks) |
| Transactions | [https://leviathandev.neptune.io/transactions](https://leviathandev.neptune.io/transactions) |
| Contracts | [https://leviathandev.neptune.io/contracts](https://leviathandev.neptune.io/contracts) |

## Assets

| Symbol | Layer | Description |
|--------|-------|-------------|
| **XNT** | Neptune L1 | Native base-layer asset |
| **WXNT** | Miden L2 | Wrapped XNT on the programmable layer (1 WXNT = 1 XNT peg intent) |

## WXNT faucet ID

Use this value in the wallet **Send Tokens** form **Faucet** field and when verifying WXNT contract state:

```
b0682b76d8939720429ec7e43f194a
```

A `0x` prefix may or may not be accepted depending on UI validation; the hex above matches pioneer documentation and request-funds examples.

## Account ID format

* Hex string shown on wallet account cards (example shape: 32 hex characters).
* Used for funding requests, sends, and explorer search (`/account/{id}`).

## Network status

* Explorer UI displays a **testnet** badge.
* Wallet connects to the hosted Miden testnet configuration bundled with the explorer deployment.
* Assets have **no real-world value**.

## Funding model (testnet)

* Pioneers share Account IDs with the team; operators mint WXNT manually.
* The wallet **Mint Tokens** panel requires the faucet private key and is not for general users.

See [Request testnet funds](../getting-started/request-funds.md).

## Bridge monitor refresh

Bridge status auto-refresh defaults to **10 seconds** on `/bridge`.

## Documentation source

This repository (`leviathan-docs`) is structured for GitBook via `SUMMARY.md` and `.gitbook.yaml`.

## Related

* [Glossary](glossary.md)
* [Send tokens](../getting-started/send-tokens.md)
* [Bridge monitor](../bridge/README.md)
