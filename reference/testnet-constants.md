# Testnet constants

Authoritative quick reference for the public Leviathan **testnet** environment. Mainnet values are out of scope.

## Hosted URLs

| Service | URL |
|---------|-----|
| Explorer (home) | [https://leviathandev.neptune.io/](https://leviathandev.neptune.io/) |
| Hosted web wallet | [https://leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet) |
| Bridge monitor | [https://leviathandev.neptune.io/bridge](https://leviathandev.neptune.io/bridge) |
| Blocks | [https://leviathandev.neptune.io/blocks](https://leviathandev.neptune.io/blocks) |
| Transactions | [https://leviathandev.neptune.io/transactions](https://leviathandev.neptune.io/transactions) |
| Contracts | [https://leviathandev.neptune.io/contracts](https://leviathandev.neptune.io/contracts) |
| Chrome extension package | Pioneers Telegram pinned message (Load unpacked; not Chrome Web Store) |

## Assets

| Symbol | Layer | Description |
|--------|-------|-------------|
| **XNT** | Neptune L1 | Native base-layer asset |
| **WXNT** | Miden L2 | Wrapped XNT on the programmable layer (1 WXNT = 1 XNT peg intent) |

## WXNT faucet ID

Use this value when a send form asks for the token **Faucet** field for WXNT:

```
b0682b76d8939720429ec7e43f194a
```

This is the faucet **contract** id on the programmable layer, not a private key and not a self-serve funding URL.

## Address formats

| Wallet | Receive display | Accepted when pasting into that wallet’s send/fund fields |
|--------|-----------------|----------------------------------------------------------|
| Leviathan Chrome extension | bech32 only (for example `mtst1…`) | bech32 |
| Hosted web wallet | Account identifier on the card | hex or bech32 |

## Network status

* Explorer UI displays a **testnet** badge.
* Pioneer Chrome extension builds target **testnet**.
* Assets have **no real-world value**.

## Funding model (testnet)

* Pioneers request funds in the **Leviathan Pioneers** Telegram group; operators mint WXNT.
* Hosted **Mint Tokens** panel is operator-only (requires faucet private key).

See [Request testnet funds](../getting-started/request-funds.md).

## Bridge monitor refresh

Bridge status auto-refresh defaults to **10 seconds** on `/bridge`.

## Documentation source

This repository (`leviathan-docs`) is structured for GitBook via `SUMMARY.md` and `.gitbook.yaml`.

## Related

* [Glossary](glossary.md)
* [Wallets overview](../wallets/README.md)
* [Send tokens](../getting-started/send-tokens.md)
* [Bridge monitor](../bridge/README.md)
