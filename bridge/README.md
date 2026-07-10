# Bridge monitor

The bridge monitor at [leviathandev.neptune.io/bridge](https://leviathandev.neptune.io/bridge) shows **settlement and activity** between Neptune L1 (native **XNT**) and the Miden programmable layer (wrapped **WXNT**).

This page is read-only monitoring. Moving value across layers uses L1 deposits, wallet burns, and proving infrastructure documented elsewhere as those flows mature on testnet.

## What the bridge does (conceptually)

| Direction | On-chain meaning (high level) |
|-----------|-------------------------------|
| **XNT → Miden** | XNT is locked on Neptune; matching **WXNT** becomes available on Miden (shown as **deposits** in the monitor) |
| **WXNT → XNT** | WXNT is burned on Miden; **XNT** is unlocked on Neptune (shown as **burns** in the monitor) |

The design target is settlement backed by **cryptographic proofs**, not a multisig custodian. On testnet, treat bridge behavior as experimental and verify outcomes on both layers when testing.

## Page layout

### Status cards

The top row refreshes automatically (default **10s** interval; toggle with **Auto-refresh**):

| Stat | Meaning |
|------|---------|
| **Miden Tip** | Latest Miden block height tracked by the bridge backend |
| **Neptune Tip** | Neptune chain tip height recorded in bridge/faucet state |
| **Checkpoint** | Bridge checkpoint height on Neptune |
| **Faucet Nonce** | WXNT faucet contract nonce on Miden |
| **Total Minted** | Cumulative WXNT minted via bridge-related activity |
| **Total Burned** | Cumulative WXNT burned toward L1 withdrawal |

### Deposits (XNT → Miden)

Recent deposits table columns:

* **Note ID** — Miden note identifier for the deposit
* **Amount** — WXNT amount (formatted with token decimals from bridge config)
* **Recipient** — Miden account receiving the minted value
* **Block** — Miden block where the deposit was observed

### Burns (WXNT → XNT)

Recent burns table columns:

* **Note ID** — note consumed in the burn
* **Amount** — WXNT burned
* **Sender** — Miden account that initiated the burn
* **Block** — Miden block height

## How pioneers use this page

* Confirm that a cross-layer operation you attempted appears in **Deposits** or **Burns**.
* Compare **Miden Tip** and **Neptune Tip** to see whether both layers are advancing.
* Cross-check **Total Minted** and **Total Burned** for rough supply movement on testnet (not a substitute for full accounting).

For programmable-layer transfers that stay on Miden, use the [wallet send flow](../getting-started/send-tokens.md) and the [explorer transaction list](../explorer/README.md) instead.

## Troubleshooting

| Issue | What to try |
|-------|-------------|
| Empty deposit/burn tables | No recent bridge events, or indexer lag; wait and refresh |
| Error banner on load | Backend or RPC unavailable; retry later |
| Activity in wallet but not on bridge | You may have done an L2-only WXNT send, not a bridge deposit/burn |

## Related reference

* WXNT faucet ID and URLs: [Testnet constants](../reference/testnet-constants.md)
* Stack overview: [Why Leviathan is built this way](../technology/overview.md)
