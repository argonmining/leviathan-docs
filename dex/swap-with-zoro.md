# Swap with Zoro

Use this guide to trade on Leviathan testnet via **Zoro**, the featured private-swap dApp in the Leviathan Chrome extension Browser.

**Prerequisites**

* [Leviathan Chrome extension](../wallets/chrome-extension.md) installed and unlocked
* Testnet funds / notes already in the wallet ([request funds](../getting-started/request-funds.md) if needed)
* Willingness to **Sync** and **Consume** after the swap so balances catch up

## Step 1 — Open the Browser

1. Open the Leviathan extension (popup or full page, depending on your build).
2. Go to the **Browser** tab (in-app dApp browser).
3. Open **Zoro** from the featured list, or navigate to [https://app.zoroswap.com/](https://app.zoroswap.com/).

The wallet ships Zoro as:

* **Name:** Zoro  
* **URL:** `https://app.zoroswap.com/`  
* **Category:** DeFi (featured)  
* **Description:** Private swaps on Miden  

## Step 2 — Connect the wallet

1. In Zoro, start the **Connect** flow when prompted.
2. Approve the connection in the Leviathan confirmation UI.
3. If the dApp asks you to register a trading key or fund a vault, follow its on-screen steps. Those are Zoro application flows, not explorer settings.

If connection fails, confirm the extension is unlocked, on **testnet**, and that you opened Zoro from the Leviathan Browser (not a random desktop tab without the wallet injected).

## Step 3 — Trade

1. Select the market / side the UI offers (buy or sell).
2. Review size, price, and any fees the dApp displays.
3. Confirm the transaction in Leviathan when asked.
4. Wait for proving / submission to finish. Heavy proves can take noticeable time on a laptop; do not close the confirmation mid-flight.

Exact markets and pool depth are defined by Zoro and can change. This documentation does **not** publish a fixed pair list or TVL figures.

## Step 4 — Sync and consume in the wallet

After a successful swap:

1. Return to the Leviathan wallet home.
2. Run **Sync** (or wait for automatic sync).
3. If notes appear as claimable, **Consume** them.
4. Confirm the new asset balances under Manage assets / home balances.

Pioneer feedback has repeatedly shown that **swaps can succeed while the wallet still shows zero** until notes are synced and consumed. Treat Sync + Consume as part of the swap, not optional cleanup.

## Troubleshooting

| Symptom | What to try |
|---------|-------------|
| dApp cannot reach vault / RPC | Zoro infrastructure issue; retry later or ask in Pioneers |
| Connect does nothing | Unlock extension; open Zoro inside Leviathan Browser |
| Swap confirmed but balance unchanged | Sync → Consume; check Activity / history for the tx |
| Unexpected token shows zero | Open Manage assets / import or reveal the faucet for that asset if the wallet supports it; ask Pioneers which faucet id to use |
| Explorer has no `/swap` page | Expected — there is no first-party Leviathan DEX URL yet |

## Boundaries

* Zoro is **not** the first-party Leviathan DEX product.
* Testnet assets have **no real-world value**.
* Do not paste seed phrases into any dApp.
* For peer transfers that are not swaps, use [Send tokens](../getting-started/send-tokens.md).

## Related

* [Swaps and DEX overview](overview.md)
* [Chrome extension](../wallets/chrome-extension.md)
* [Explorer](../explorer/README.md)
