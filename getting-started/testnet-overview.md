# Testnet overview

Leviathan is **testnet only** right now. There is no mainnet deployment described in this documentation, and testnet assets have **no real world value**.

## What you can do today

* Browse blocks, transactions, accounts, and contracts on the [explorer](https://leviathandev.neptune.io/)
* Install the **[Leviathan Chrome extension](../wallets/chrome-extension.md)** ([download v1.14.0](https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-09-29/leviathan-chrome-testnet.zip))
* Optionally use the [hosted web wallet](https://leviathandev.neptune.io/wallet)
* Get testnet funds by asking in the **Leviathan Pioneers** Telegram group
* Send assets between accounts you control
* Monitor bridge activity between Neptune L1 and Miden L2
* Builders with a terminal can use **`leviathan-client`** with [delegated TEE proving](../tee/overview.md)
* Chat with [Private AI](https://ai-tee-leviathan.up.railway.app/) — open-weight models inside attested TEEs, E2EE prompts, wallet or card credits ([chat UI](../confidential-ai/chat-ui.md))
* Swap on **[NeptuneSwap](../dex/overview.md)** at [testnet.zkswap.ai](https://testnet.zkswap.ai/) (then **Sync** and **Consume** notes in the wallet)

## What you need

* Google Chrome (for the extension) or a modern browser (for the hosted wallet / explorer / Private AI)
* The [official Chrome extension zip](https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-09-29/leviathan-chrome-testnet.zip)
* Time to Sync and Consume notes after funding

## Testnet vs mainnet

The explorer shows a **testnet** badge. Wallet builds are aimed at testnet. Do not expect mainnet addresses, assets, or balances to work here.

## Assets on testnet

| Asset | Layer | Role |
|-------|-------|------|
| **XNT** | Neptune L1 | Native privacy layer asset (base chain) |
| **WXNT** | Miden L2 | Wrapped XNT on the programmable layer (1 WXNT = 1 XNT peg intent) |

Most pioneer activity happens on the **programmable layer**. L1 operations that require a local Neptune node are outside the basic getting-started path.

## Work in progress

This is an active testnet. Expect downtime, UI changes, and items still listed under [Coming soon](../coming-soon/README.md). Report issues in the Pioneers channel.

## Next steps

1. [Install the Chrome extension](../wallets/chrome-extension.md) (or [hosted web wallet](../wallets/web-wallet.md))
2. [Request testnet funds](request-funds.md)
3. [Send tokens](send-tokens.md) or [swap on NeptuneSwap](../dex/swap.md)
