# Why Leviathan is built this way

Leviathan is a **two-layer stack** with a **cryptographic bridge** between them. The split is intentional: privacy and native value on one layer, general programmability on the other, without forcing every application to choose only one model.

## Neptune L1 — private base layer

Neptune is the **base layer** where the native asset **XNT** lives. Instead of a fully transparent account ledger, Neptune uses a **private accounting model** (mutator set) so the chain can validate transfers without publishing balances and counterparties by default.

Validity is enforced with **STARK proofs** produced by the **Triton** VM. Nodes verify proofs; they do not re-execute private transaction data in the open.

## Miden L2 — programmable layer

Miden is the **programmable layer** where applications run. Key design choices:

* **Accounts are state machines** — each account has its own code and storage.
* **Interaction via notes** — assets and scripts move as notes between accounts, not only as direct contract calls on shared global state.
* **Client-side proving** — wallets and clients execute and prove transactions locally; the network verifies proofs.

On Leviathan testnet, the bridged representation of XNT on Miden is **WXNT** (wrapped XNT), pegged 1:1 in intent.

## The bridge

The bridge connects the layers:

* **Into Miden** — lock XNT on Neptune; WXNT becomes available on Miden.
* **Out of Miden** — burn WXNT; unlock XNT on Neptune.

The goal is **proof-backed settlement** rather than trusting a small signer set. On testnet, the bridge is the most experimental surface — use the [bridge monitor](../bridge/README.md) and treat outcomes as something to validate, not assume.

## Why not one chain?

A single transparent smart-contract chain makes every balance and call pattern visible by default. Leviathan separates concerns:

| Need | Layer |
|------|--------|
| Private store of value, long-term holdings | Neptune (XNT) |
| Apps, swaps, structured payments, experimentation | Miden (WXNT and other assets) |
| Move value between models | Bridge |

Builders can hold value privately on L1, bring working capital to L2 as WXNT, and return settlement to L1 when the application requires it.

## What testnet proves

The public testnet at [leviathandev.neptune.io](https://leviathandev.neptune.io/) exercises:

* Miden indexing and explorer UX
* Leviathan Chrome extension (Pioneers sideload) and hosted browser wallet
* WXNT funding via Pioneers Telegram (operator mint) and peer-to-peer sends
* Bridge visibility and settlement plumbing
* Delegated STARK proving in an attested TEE for `leviathan-client` workflows

It does **not** yet imply production-ready mainnet economics, a live DEX, or final bridge parameters.

## Read next

* [Privacy by design](privacy.md)
* [STARK proofs](stark-proofs.md)
* [Post-quantum cryptography](post-quantum.md)
* [TEE proving overview](../tee/overview.md)
* [Glossary](../reference/glossary.md)
