# STARK proofs

Both layers of Leviathan rely on **succinct transparent arguments of knowledge (STARKs)** to scale verification: nodes check cryptographic proofs instead of re-running full private computation in the clear.

## What a STARK gives you

A STARK lets a prover convince verifiers that a computation was executed correctly, with:

* **Transparency** — no trusted setup ceremony for the proof system (unlike some SNARK constructions)
* **Post-quantum friendly hashing** — STARK security is rooted in hash functions and Reed–Solomon techniques rather than elliptic-curve pairings for the proof layer
* **Scalable verification** — verification time grows slowly compared to execution size

In Leviathan, the important user-facing idea is simpler: **the chain checks a proof that the rules were followed**, not every secret input behind the transaction.

## Neptune and Triton

On Neptune L1, transaction validity is expressed as STARK proofs over programs executed in the **Triton** virtual machine. Private inputs stay with the prover; the chain sees commitments, public inputs, and the proof.

## Miden and client-side proving

On the programmable layer, **wallets and clients prove account transitions locally** (state updates, note consumption, script execution). Miden validators verify those proofs. This is why pioneer sends in the browser wallet can feel like “sign and wait” while heavy work happens on your machine.

When local proving is too heavy, Leviathan testnet also supports **delegated proving inside an attested TEE**. The client still builds and submits the transaction; the enclave generates the STARK. See [TEE proving overview](../tee/overview.md) and [Attestation and trust](../tee/attestation.md).

## STARKs vs trust

STARKs reduce trust in **honest execution** — they do not remove the need for:

* Correct **protocol rules** and implementations
* Secure **key handling** in the wallet
* Sound **bridge logic** between L1 and L2

On testnet, proof systems and circuits are still under active development. Occasional failures or version upgrades are expected.

## Further reading

* Stack context: [overview](overview.md)
* Hashing and signature choices: [post-quantum cryptography](post-quantum.md)
* [Glossary](../reference/glossary.md) — proof, note, mutator set
