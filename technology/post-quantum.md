# Post-quantum cryptography

Leviathan is designed with **long-lived security** in mind. That includes planning for cryptographically relevant quantum computers, which would break many widely deployed elliptic-curve schemes.

## Design stance

* **Proof layer** — STARK-based verification on Neptune (via Triton) relies on hash-based and algebraic techniques that are not vulnerable to Shor’s algorithm in the same way ECDSA is.
* **Signatures and addresses on Neptune** — the Neptune stack supports **multiple address types** with different cryptographic assumptions, including options aimed at post-quantum security (for example hash-based and lattice-oriented constructions used in the broader Neptune codebase).
* **Programmable layer accounts** — testnet wallet accounts use **Falcon512** with Poseidon2 for authentication components (see wallet “Public wallet with Falcon512 auth”). This reflects Miden’s current component library; it is not the same as Neptune L1 address formats.

Pioneers should use the **wallet and address types documented for each layer** rather than assuming one key type everywhere.

## What pioneers should do

| Layer | Practical guidance |
|-------|---------------------|
| **Miden / WXNT** | Use the browser wallet; back up Account IDs and `.mac` exports |
| **Neptune / XNT** | Follow Neptune node and wallet docs for L1 addresses when you run local infrastructure |
| **Bridge** | Treat cross-layer moves as high-risk experiments on testnet |

## Limitations

* **Testnet only** — algorithms and parameters may change before any mainnet.
* **PQ-ready ≠ PQ-complete** — every dependency (libraries, hardware, operational practices) must align for end-to-end quantum resistance.
* **Hybrid transition** — ecosystems often support legacy and PQ-oriented schemes in parallel during migration; check current release notes in upstream Neptune and Miden repositories for exact support matrices.

## Related topics

* [STARK proofs](stark-proofs.md)
* [Privacy by design](privacy.md)
* [Glossary](../reference/glossary.md)
