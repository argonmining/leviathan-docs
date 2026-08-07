# NeptuneSwap (testnet DEX)

**NeptuneSwap** is the live private DEX on Leviathan testnet. It was announced to Pioneers as a private, post-quantum DEX for swapping on the programmable layer.

| | |
|--|--|
| **URL** | [https://testnet.zkswap.ai/](https://testnet.zkswap.ai/) |
| **Product** | NeptuneSwap – DeFi on Leviathan |
| **Network** | Leviathan testnet (UI footer shows e.g. `Leviathan testnet 0.15.0`) |
| **Status** | Live for pioneers — UI, pools, and pairs can change without notice |

This is **not** a route on [leviathandev.neptune.io](https://leviathandev.neptune.io/) (paths like `/swap` there remain 404). Use the `testnet.zkswap.ai` host above.

## What you can do

| Page | Path | Purpose |
|------|------|---------|
| **Swap** | `/` | Market swaps (and a **Limit** tab when the deployment enables it) |
| **Pools** | `/pools` | Browse liquidity pools (TVL / cap, pool size); connect a wallet for your positions |
| **Faucet** | `/faucet` | Mint **test** tokens for the NeptuneSwap AMM into a connected wallet |
| **History** | `/history` | Activity for your connected wallet (swaps, deposits, withdrawals, limit orders) |

Pricing on swaps is described in-product as a **PMM curve** (Pragma oracle price + pool inventory), executed on-chain in the Leviathan VM, minus pool fees. Exact pairs and depth change as pools are registered — do not treat any pair list in chat as permanent.

## Wallet

1. Install and unlock the [Leviathan Chrome extension](../wallets/chrome-extension.md).
2. Open [testnet.zkswap.ai](https://testnet.zkswap.ai/) and click **Connect**.
3. Choose **Leviathan Wallet** when prompted and approve in the extension.

You need spendable testnet assets first ([request funds](../getting-started/request-funds.md) and/or use the [DEX faucet](faucet-and-pools.md)).

## Notes after every trade (required)

Swaps, minting, and transfers create **notes**. Balances in the wallet often stay at zero until you:

1. **Sync** the wallet with the chain
2. **Consume** (claim) claimable notes so assets move into spendable balance

Pioneer feedback after going live repeatedly hit this: the swap can succeed while the home screen still shows zero for ETH, SOL, and other assets. Treat Sync → Consume as part of the trade, not optional cleanup. NeptuneSwap activity copy also points you to **claim in the wallet**.

## What this documentation does not publish

* On-chain pool / faucet **contract IDs** (not published as an official constants table yet — ask in Pioneers if you need a specific id)
* Guaranteed limit-order availability (the Limit tab can show unavailable when the deployment has no read service / matching note scripts)
* Mainnet economics or permanent TVL figures from the pools UI

## Related

* [How to swap](swap.md)
* [Faucet and pools](faucet-and-pools.md)
* [Chrome extension](../wallets/chrome-extension.md)
* [Send tokens](../getting-started/send-tokens.md) (peer transfers, not AMM swaps)
* [Testnet constants](../reference/testnet-constants.md)
