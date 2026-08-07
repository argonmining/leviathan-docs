# How to swap on NeptuneSwap

Trade on [https://testnet.zkswap.ai/](https://testnet.zkswap.ai/) with the Leviathan Chrome extension. Testnet assets have **no real-world value**.

## Prerequisites

* [Leviathan Chrome extension](../wallets/chrome-extension.md) installed, unlocked, on testnet
* Spendable balance (from [Pioneers funding](../getting-started/request-funds.md) and/or the [NeptuneSwap faucet](faucet-and-pools.md))
* Willingness to **Sync** and **Consume** after the swap

## Step 1 — Connect

1. Open [https://testnet.zkswap.ai/](https://testnet.zkswap.ai/).
2. Click **Connect**.
3. Select **Leviathan Wallet** and approve in the extension.

If connect does nothing, unlock the extension and retry in the same browser profile that has Leviathan loaded.

## Step 2 — Place a market swap

1. Stay on **Swap** (home). Use the **Swap** tab (not Limit) unless you intentionally want a resting order.
2. Choose **SELL** and **BUY** assets from the token selectors.
3. Enter an amount. Review the quoted rate, pool depth hints, slippage, and any fee copy the UI shows.
4. Confirm when prompted. Proving can take several seconds — keep the tab open until the wallet returns a transaction id.

Default slippage is configurable in the UI. If the on-chain fill would be worse than your slippage floor, the swap can **refund** instead of completing.

## Step 3 — Sync and consume in the wallet

After a successful swap:

1. Return to the Leviathan wallet home.
2. Run **Sync** (or wait for automatic sync).
3. **Consume** claimable notes.
4. Confirm balances under home / manage assets.

If you swapped into an asset that still shows zero, Sync → Consume first before assuming the trade failed. Activity on NeptuneSwap (**History**) can show the order while the wallet still needs a claim.

## Limit orders (optional)

The UI has a **Limit** tab. Limit orders escrow an asset and rest until the pool can fill at your price, the deadline passes, or you cancel/reclaim.

On some deployments Limit shows **unavailable** (for example when a read service is not configured). If that happens, use market **Swap** only.

## Troubleshooting

| Symptom | What to try |
|---------|-------------|
| Connect fails | Unlock Leviathan; same Chrome profile; reload the dApp |
| “Insufficient liquidity” | Smaller size or another pair; check [Pools](faucet-and-pools.md) |
| Swap confirmed, balance still zero | Sync → Consume; check wallet Activity and NeptuneSwap **History** |
| Unexpected token missing | Manage assets / ask Pioneers which faucet id to reveal for that asset |
| Proving hangs | Keep the confirmation open; heavy proves can take noticeable time |
| Gas / fee hard to see in UI | Known pioneer feedback — still complete Sync → Consume; ask in Pioneers if stuck |

## Related

* [NeptuneSwap overview](overview.md)
* [Faucet and pools](faucet-and-pools.md)
* [Send tokens](../getting-started/send-tokens.md)
