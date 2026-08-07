# Glossary

Terms used across Leviathan testnet documentation.

## A

**Account (Miden)** — A programmable entity with code, storage, and a vault. Identified by a hex **Account ID**. Wallets create accounts with authentication components (testnet default: Falcon512).

**Account ID** — Identifier for a Miden account. Hosted web wallet shows hex on account cards and accepts hex or bech32 in relevant fields. The Chrome extension **Receive** screen shows **bech32** only (for example `mtst1…`).

**Attestation** — Cryptographic evidence that a specific software composition is running inside a genuine TEE. Leviathan clients fetch attestation before delegated proving and pin the enclave TLS certificate. Confidential AI publishes gateway attestation reports for the same class of check. See [Attestation and trust](../tee/attestation.md) and [Verify Confidential AI](../confidential-ai/verify.md).

## B

**Bridge** — Mechanism that moves value between Neptune L1 (**XNT**) and Miden L2 (**WXNT**). Monitored at `/bridge` on the testnet explorer.

**Burn (WXNT)** — Destroying WXNT on Miden as part of withdrawing to XNT on Neptune. Listed in the bridge monitor burns table.

## C

**Claimable** — Notes or assets the wallet knows about but have not yet been **consumed** into the spendable balance.

**Compose hash** — Expected enclave measurement (related to runtime registers such as RTMR3) configured in `tee_compose_hash`. Clients reject delegated proving if the live enclave does not match. Updates when the TEE image or CVM is redeployed.

**Confidential AI** — Testnet LLM product: chat with `gpt-oss-120b` inside attested TEEs, metered by prepaid `lev_` API key credits. Hosted UI: [ai-tee-leviathan.up.railway.app](https://ai-tee-leviathan.up.railway.app/). See [Confidential AI overview](../confidential-ai/overview.md).

**Consume** — Wallet action that processes claimable notes so balances update.

**Contract** — On-chain Miden program with an ID browseable under **Contracts** in the explorer.

**Credits (Confidential AI)** — Off-chain prepaid units on the auth service. New keys start at 0; each successful chat costs 1 credit. Top up via NOWPayments (sandbox on testnet). See [Credits and NOWPayments](../confidential-ai/credits.md).

## D

**Delegate proving** — Client flag (`--delegate-proving`) that sends STARK proof generation to a remote TEE prover instead of proving only on the local machine. See [Set up delegated TEE proving](../tee/setup.md).

**Deposit (bridge)** — L1 XNT locked on Neptune corresponding to WXNT minted on Miden; shown in bridge **Deposits**.

## E

**E2EE (ACI v2)** — End-to-end encryption for Confidential AI: client seals prompts to an attested X25519 key from the gateway keyset; the metering Edge relays ciphertext. The chat UI enables this by default.

**Edge** — Metering front for Confidential AI (`leviathan-edge.duckdns.org` on testnet). Forwards chat to the gateway TEE after credit checks.

## F

**Faucet (WXNT)** — On-chain contract id for testnet WXNT (`b0682b76d8939720429ec7e43f194a`), used when a send form asks which token faucet to spend from. Pioneers receive funds by requesting a mint in the Pioneers Telegram group; the hosted **Mint Tokens** panel is operator-only.

## G

**gpt-oss-120b** — Open-weight (Apache 2.0) model id served by Confidential AI on testnet. See [The model](../confidential-ai/model.md).

## M

**Miden** — Programmable layer (L2) used by Leviathan testnet for accounts, notes, and proofs.

**Mutator set** — Neptune data structure for private ownership and spends; commitments replace transparent account balances on L1.

## N

**Neptune** — Privacy-oriented base layer (L1) for native **XNT**.

**NeptuneSwap** — Live private DEX on Leviathan testnet at [testnet.zkswap.ai](https://testnet.zkswap.ai/). Connect the Leviathan Chrome extension; after swaps use **Sync** and **Consume**. See [NeptuneSwap overview](../dex/overview.md).

**Note** — Miden message that can carry assets and consumption rules; accounts interact by creating and consuming notes. Swaps and faucet mints create notes that must be consumed before balances look updated.

**Nonce** — Counter associated with an account or contract; advances as state updates are executed.

**NOWPayments** — Payment provider used for Confidential AI credit checkout. Testnet uses **sandbox** completion (do not send real funds). See [Credits and NOWPayments](../confidential-ai/credits.md).

## P

**Phala Cloud** — Hosting platform for Confidential VMs used by the Leviathan testnet TEE prover (Intel TDX / dstack).

**Pioneer** — Early testnet participant using Leviathan interfaces and providing feedback.

**PMM (NeptuneSwap)** — Pricing model used by NeptuneSwap pools (Pragma oracle price + pool inventory), run on-chain in the Leviathan VM.

**Proof (STARK)** — Succinct argument that a computation or transaction followed protocol rules, verified without exposing private inputs.

## R

**Receipt (Confidential AI)** — TEE-signed record of a chat exchange, identified by `x-receipt-id`, retrievable only by the issuing API key.

## S

**Sync** — Wallet action that pulls the latest chain state into the browser session.

## T

**TDX** — Intel Trust Domain Extensions; TEE technology used for the Phala-hosted remote prover and for Confidential AI’s gateway / model confidential compute stack.

**TEE** — Trusted Execution Environment: hardware-isolated enclave. On Leviathan testnet this covers (1) remote STARK proving and (2) Confidential AI inference. See [TEE proving overview](../tee/overview.md) and [Confidential AI overview](../confidential-ai/overview.md).

**Testnet** — Non-production network with no real-world asset value. Badge shown in the explorer header.

**Triton** — Virtual machine on Neptune used to generate and verify STARK proofs for L1 transactions.

## W

**Wallet (browser)** — Hosted at `/wallet` on leviathandev; stores keys in browser storage (IndexedDB). Secondary to the Chrome extension for pioneers.

**Wallet (Chrome extension)** — **Leviathan** unpacked extension distributed via the Pioneers Telegram pin. Primary pioneer wallet; Receive addresses are bech32. Not used to sign into Confidential AI today.

**WXNT** — Wrapped XNT on Miden. Testnet programmable-layer asset; 1:1 peg intent with XNT.

**XNT** — Native asset on Neptune L1.
