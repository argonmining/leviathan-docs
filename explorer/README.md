# Explorer guide

The public Leviathan testnet explorer is hosted at [leviathandev.neptune.io](https://leviathandev.neptune.io/). It indexes the **Miden programmable layer** (blocks, transactions, accounts, and contracts) and links to the in-browser wallet.

The header shows a **testnet** badge. Data and URLs here do not apply to mainnet.

## Navigation

| Page | Path | Purpose |
|------|------|---------|
| **Overview** | `/` | Chain summary, recent blocks, and latest transactions |
| **Blocks** | `/blocks` | Paginated block list |
| **Transactions** | `/transactions` | Recent Miden transactions |
| **Bridge** | `/bridge` | XNT ↔ WXNT bridge monitor (see [Bridge monitor](../bridge/README.md)) |
| **Contracts** | `/contracts` | On-chain contracts, including the WXNT faucet |
| **Wallet** | `/wallet` | Browser wallet (see [Create a wallet](../getting-started/create-wallet.md)) |

Use the theme toggle in the header for light or dark mode.

## Search

The search bar accepts several identifier types:

* **Block number** — numeric height (for example `42`)
* **Transaction ID** — hex transaction hash
* **Account ID** — hex account identifier (with or without `0x`)

Submitting a valid query opens the matching detail page (`/block/{n}`, `/tx/{id}`, or `/account/{id}`).

## Detail pages

### Block (`/block/{number}`)

Shows block metadata and the transactions included in that block. Click a transaction row to open its detail view.

### Transaction (`/tx/{id}`)

Shows transaction ID, block context, and related fields exposed by the indexer. Use this after [sending tokens](../getting-started/send-tokens.md) to confirm your transfer landed.

### Account (`/account/{id}`)

Shows account state visible on the programmable layer: nonce, vault assets, and recent activity where indexed. This complements the wallet UI, which also tracks private notes and claimable balances locally.

### Contract (`/contracts` and contract detail)

Browse deployed contracts. The WXNT faucet contract is central to testnet WXNT; its ID is listed in [Testnet constants](../reference/testnet-constants.md).

## Typical pioneer flows

1. **Verify a send** — copy the transaction ID from the wallet after **Send**, search or open **Transactions**, then open the tx detail page.
2. **Inspect an account** — paste your wallet Account ID into search to see on-chain account state.
3. **Watch bridge activity** — open **Bridge** for deposits (XNT → Miden) and burns (WXNT → XNT).

## Limits

The explorer reflects what the indexer has processed. There can be short lag after a wallet **Sync**. If something is missing, sync the wallet again and retry in a minute.

Operator-only actions (manual mint, L1 node setup) are not fully represented in the explorer UI. Pioneer funding goes through [request testnet funds](../getting-started/request-funds.md).
