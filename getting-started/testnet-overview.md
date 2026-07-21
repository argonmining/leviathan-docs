# Testnet overview

Leviathan is **testnet only** right now. There is no mainnet deployment described in this documentation, and testnet assets have **no real world value**.

## What you can do today

* Browse blocks, transactions, accounts, and contracts on the [explorer](https://leviathandev.neptune.io/)
* Use the **Leviathan Chrome extension** (primary pioneer wallet — sideload from Pioneers Telegram)
* Optionally use the [hosted web wallet](https://leviathandev.neptune.io/wallet)
* Get testnet funds via the extension **Faucet** flow (team mint as fallback)
* Send assets between accounts you control
* Monitor bridge activity between Neptune L1 and Miden L2
* Builders with a terminal can use **`leviathan-client`** with [delegated TEE proving](../tee/overview.md)

## What you need

* Google Chrome (for the extension) or a modern browser (for the hosted wallet / explorer)
* Access to the **Leviathan Pioneers Telegram** group for the pinned extension package
* Time to Sync and Consume notes after funding

## Testnet vs mainnet

The explorer shows a **testnet** badge. Pioneer wallet builds are aimed at testnet. Do not expect mainnet addresses, assets, or balances to work here.

## Assets on testnet

| Asset | Layer | Role |
|-------|-------|------|
| **XNT** | Neptune L1 | Native privacy layer asset (base chain) |
| **WXNT** | Miden L2 | Wrapped XNT on the programmable layer (1 WXNT = 1 XNT peg intent) |

Most pioneer activity happens on the **programmable layer**. L1 operations that require a local Neptune node are outside the basic getting-started path.

## Work in progress

This is an active testnet. Expect downtime, UI changes, and features still listed under [Coming soon](../coming-soon/README.md) (notably the DEX). Report issues in the Pioneers channel.

## Next steps

1. [Install the Chrome extension](../wallets/chrome-extension.md) (or [hosted web wallet](../wallets/web-wallet.md))
2. [Get testnet funds](request-funds.md)
3. [Send tokens](send-tokens.md)
