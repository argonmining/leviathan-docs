# Privacy by design

Leviathan treats privacy as a **default property of the base layer** and a **configurable property of the programmable layer**, not as an optional mixer bolted on later.

## Neptune: private by default

On Neptune L1, ownership and spends are represented with **cryptographic commitments** in a **mutator set** rather than as open account balances. The network checks that transactions are valid — including conservation of value and authorization — without requiring public disclosure of who paid whom.

What remains visible on L1 is what the protocol needs for consensus and verification (for example, proof data and commitments), not a full financial graph of every user.

## Miden: private execution, public verification

On the programmable layer, **accounts execute locally** and submit **proofs** to the network. The chain verifies that execution followed the rules; it does not need to replay every private input on every node.

Practical effects for pioneers on testnet:

* Wallet balances and notes are managed in the **browser wallet**; the explorer shows **on-chain account state** the indexer knows about.
* **Claimable notes** may exist before you click **Consume** — that is part of the note-based asset model.
* Application designers can keep sensitive logic and data on the client while still producing verifiable proofs.

## What privacy does not mean

* **Not anonymity against everyone** — validators and indexers see what the protocol emits; pioneers should not treat testnet as a shield against lawful or operational monitoring.
* **Not hidden from yourself** — you still hold keys and export `.mac` files; backup discipline matters.
* **Not uniform across layers** — L1 and L2 have different visibility models; bridge events may appear in the [bridge monitor](../bridge/README.md).

## Composing L1 and L2 privacy

A common pattern:

1. Hold XNT on Neptune when you want base-layer privacy.
2. Bridge to WXNT for application interaction on Miden.
3. Bridge back when you want funds on the base layer again.

Each hop has its own visibility footprint. Plan flows accordingly when designing apps or demos.

## Related topics

* [Why Leviathan is built this way](overview.md)
* [STARK proofs](stark-proofs.md) — how validity is checked without exposing secrets
* [Glossary](../reference/glossary.md) — notes, accounts, WXNT
