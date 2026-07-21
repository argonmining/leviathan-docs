# Testnet overview

Leviathan is **testnet only** right now. There is no mainnet deployment described in this documentation, and testnet assets have **no real world value**.

## What you can do today

On the public testnet explorer you can:

* Browse blocks, transactions, accounts, and contracts
* Create browser wallets and hold WXNT (wrapped testnet XNT on the programmable layer)
* Send WXNT between accounts you control
* Monitor bridge activity between Neptune L1 and Miden L2

Builders with a terminal can also use **`leviathan-client`** with **delegated TEE proving** — prove heavy transactions inside an attested enclave instead of only on your laptop. See [TEE proving overview](../tee/overview.md) and the [setup guide](../tee/setup.md).

## What you need

* A modern browser (Chrome, Firefox, or Safari)
* Access to [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet)
* A wallet account ID to share with the team when requesting testnet funds

## Testnet vs mainnet

The explorer header shows a **testnet** badge. The wallet connects to the Miden testnet network automatically when you use the hosted explorer. Do not expect mainnet addresses, assets, or balances to work here.

## Assets on testnet

| Asset | Layer | Role |
|-------|-------|------|
| **XNT** | Neptune L1 | Native privacy layer asset (base chain) |
| **WXNT** | Miden L2 | Wrapped XNT on the programmable layer (1 WXNT = 1 XNT peg intent) |

Most pioneer activity happens on the **programmable layer** using WXNT in the browser wallet. L1 operations require running a Neptune node locally and are not covered in the basic getting started path.

## Work in progress

This is an active testnet. You may see downtime, interface changes, or features that are documented as coming soon. That is expected. Report issues to the team through your pioneer channel.

## Next steps

1. [Create a wallet](create-wallet.md)
2. [Request testnet funds](request-funds.md)
3. [Send tokens](send-tokens.md) between your accounts
