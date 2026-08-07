# Swaps and DEX on testnet

Pioneers can already **swap assets on the programmable layer** through a featured third-party DEX. A **first-party Leviathan DEX** (hosted under `leviathandev.neptune.io`, with Leviathan-published contract IDs) is **not** live yet.

| Path | Status | How pioneers use it |
|------|--------|---------------------|
| **Zoro** (`app.zoroswap.com`) | Live as a featured dApp in the Leviathan wallet Browser | Open Browser → Zoro → connect wallet → trade |
| **First-party Leviathan DEX** | Not published | No explorer `/swap` route; no official contract IDs in this documentation |

This section documents what you can do **today**, with honest boundaries.

## What “DEX” means here

On Leviathan testnet, swaps run as **Miden account / note transactions**. Your wallet constructs and proves (or confirms) the transaction; the network verifies proofs. That is the same proving model as [send tokens](../getting-started/send-tokens.md), applied to a trading dApp instead of a peer transfer.

There is **no** Leviathan-operated AMM page on the explorer today (`/swap` and `/dex` on [leviathandev.neptune.io](https://leviathandev.neptune.io/) return 404).

## Zoro (available now)

[Zoro](https://app.zoroswap.com/) is listed in the Leviathan Chrome extension as a **featured DeFi** dApp with the tagline “Private swaps on Miden.” That listing is the authoritative in-product pointer pioneers should use.

* **URL:** [https://app.zoroswap.com/](https://app.zoroswap.com/)
* **Access:** Leviathan extension → **Browser** tab → open **Zoro** (or paste the URL)
* **Wallet connection:** Connect when the dApp prompts. Leviathan is the pioneer wallet for this testnet path; follow the connect UI the dApp shows.
* **After a swap:** return to the wallet, **Sync**, then **Consume** claimable notes so balances update

Step-by-step: [Swap with Zoro](swap-with-zoro.md).

Zoro is a **third-party** application. Pool availability, RPC reachability, and UI copy are controlled by that product. If the dApp reports vault / RPC errors, wait or ask in Pioneers — that is not an explorer outage and not a missing Leviathan `/swap` page.

## First-party Leviathan DEX (not live)

When a Leviathan-hosted DEX ships, expect:

* An announced URL in Pioneers Telegram and an update to this documentation
* Published contract / faucet IDs in [testnet constants](../reference/testnet-constants.md)
* Pioneer-facing swap UI integrated with the same wallet flows already used for send / consume

Until those are published, **do not assume** a native DEX URL or pair list exists.

## Related

* [Swap with Zoro](swap-with-zoro.md)
* [Install the Chrome extension](../wallets/chrome-extension.md)
* [Send tokens](../getting-started/send-tokens.md)
* [Testnet overview](../getting-started/testnet-overview.md)
