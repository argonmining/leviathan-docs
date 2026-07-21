# Glossary

Terms used across Leviathan testnet documentation.

## A

**Account (Miden)** — A programmable entity with code, storage, and a vault. Identified by a hex **Account ID**. Wallets create accounts with authentication components (testnet default: Falcon512).

**Account ID** — Hex identifier for a Miden account. Shown on wallet account cards; used for funding requests and sends.

**Attestation** — Cryptographic evidence that a specific software composition is running inside a genuine TEE. Leviathan clients fetch attestation before delegated proving and pin the enclave TLS certificate. See [Attestation and trust](../tee/attestation.md).

## B

**Bridge** — Mechanism that moves value between Neptune L1 (**XNT**) and Miden L2 (**WXNT**). Monitored at `/bridge` on the testnet explorer.

**Burn (WXNT)** — Destroying WXNT on Miden as part of withdrawing to XNT on Neptune. Listed in the bridge monitor burns table.

## C

**Claimable** — Notes or assets the wallet knows about but have not yet been **consumed** into the spendable balance.

**Compose hash** — Expected enclave measurement (related to runtime registers such as RTMR3) configured in `tee_compose_hash`. Clients reject delegated proving if the live enclave does not match. Updates when the TEE image or CVM is redeployed.

**Consume** — Wallet action that processes claimable notes so balances update.

**Contract** — On-chain Miden program with an ID browseable under **Contracts** in the explorer.

## D

**Delegate proving** — Client flag (`--delegate-proving`) that sends STARK proof generation to a remote TEE prover instead of proving only on the local machine. See [Set up delegated TEE proving](../tee/setup.md).

**Deposit (bridge)** — L1 XNT locked on Neptune corresponding to WXNT minted on Miden; shown in bridge **Deposits**.

## F

**Faucet (WXNT)** — Contract that mints testnet WXNT. Public ID: `b0682b76d8939720429ec7e43f194a`. Operator minting requires the faucet private key; pioneers request funds manually.

## M

**Miden** — Programmable layer (L2) used by Leviathan testnet for accounts, notes, and proofs.

**Mutator set** — Neptune data structure for private ownership and spends; commitments replace transparent account balances on L1.

## N

**Neptune** — Privacy-oriented base layer (L1) for native **XNT**.

**Note** — Miden message that can carry assets and consumption rules; accounts interact by creating and consuming notes.

**Nonce** — Counter associated with an account or contract; advances as state updates are executed.

## P

**Phala Cloud** — Hosting platform for Confidential VMs used by the Leviathan testnet TEE prover (Intel TDX / dstack).

**Pioneer** — Early testnet participant using Leviathan interfaces and providing feedback.

**Proof (STARK)** — Succinct argument that a computation or transaction followed protocol rules, verified without exposing private inputs.

## S

**Sync** — Wallet action that pulls the latest chain state into the browser session.

## T

**TDX** — Intel Trust Domain Extensions; the TEE technology used for the current Phala-hosted Leviathan remote prover.

**TEE** — Trusted Execution Environment: hardware-isolated enclave for running code (here, remote STARK proving) with attestation. See [TEE proving overview](../tee/overview.md).

**Testnet** — Non-production network with no real-world asset value. Badge shown in the explorer header.

**Triton** — Virtual machine on Neptune used to generate and verify STARK proofs for L1 transactions.

## W

**Wallet (browser)** — Hosted at `/wallet` on leviathandev; stores keys in browser storage (IndexedDB).

**WXNT** — Wrapped XNT on Miden. Testnet programmable-layer asset; 1:1 peg intent with XNT.

**XNT** — Native asset on Neptune L1.
