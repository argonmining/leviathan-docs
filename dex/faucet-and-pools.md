# NeptuneSwap faucet and pools

Companion pages on [testnet.zkswap.ai](https://testnet.zkswap.ai/) for minting swap tokens and inspecting liquidity.

## Faucet

**URL:** [https://testnet.zkswap.ai/faucet](https://testnet.zkswap.ai/faucet)

In-product copy: **Testnet faucet for the NeptuneSwap AMM.** Connect a wallet, then mint **test** tokens into that wallet for trading on NeptuneSwap.

This faucet is separate from:

* Operator **WXNT** mints in [Pioneers Telegram](../getting-started/request-funds.md)
* The hosted web wallet **Mint Tokens** panel (operator-only; needs the WXNT faucet private key)

After minting, **Sync** and **Consume** in the Leviathan wallet so faucet notes become spendable before you swap.

Not every listed asset is necessarily mintable (“Not available from faucet” appears for some selections). Limits and available tokens are defined by the live UI — this documentation does not hard-code mint caps.

## Pools

**URL:** [https://testnet.zkswap.ai/pools](https://testnet.zkswap.ai/pools)

**Liquidity Pools** lists registered pools (search / sort in the UI). Typical columns include pool asset, **TVL / cap**, and **pool size**. Connect a wallet to see your positions (supplied value and PnL once the indexer has caught up).

Pool registration and depth change over time. Pioneer sessions have seen multiple assets (for example BTC, ETH, SOL, and others) appear as pools or swap targets — treat the live table as source of truth, not this paragraph.

If the page says pools are empty, none are registered yet for that deployment; check Pioneers Telegram for redeploy notices.

## History

**URL:** [https://testnet.zkswap.ai/history](https://testnet.zkswap.ai/history)

Shows swaps, deposits, withdrawals, and limit-order activity for the **connected** wallet. Useful when a trade succeeded but wallet balances still need Sync → Consume.

## Related

* [NeptuneSwap overview](overview.md)
* [How to swap](swap.md)
* [Request testnet funds](../getting-started/request-funds.md) (WXNT / operator mint)
* [Testnet constants](../reference/testnet-constants.md)
