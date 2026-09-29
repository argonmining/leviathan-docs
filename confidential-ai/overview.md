# Confidential AI overview

Leviathan Confidential AI lets you chat with a large language model whose **prompts are processed inside hardware Trusted Execution Environments (TEEs)** — an Intel TDX gateway and an NVIDIA GPU-TEE model node — with optional **end-to-end encryption** so even the metering edge never sees plaintext.

This is a **testnet** surface. Credits are prepaid and billed off-chain. Assets and payments used in the sandbox checkout have **no production settlement meaning** for pioneers testing the flow.

## Two TEE stories (do not conflate them)

Leviathan uses TEEs in more than one place. They solve different problems:

| Path | What runs in the TEE | Who uses it | Docs |
|------|----------------------|-------------|------|
| **Delegated proving** | STARK proof generation for Miden transactions | `leviathan-client` with `--delegate-proving` | [TEE proving overview](../tee/overview.md) |
| **Confidential AI** | LLM inference (gateway + model node) | Browser UI or OpenAI-compatible API | This section |

Both rely on hardware isolation and attestation. Neither replaces on-chain STARK verification, and neither eliminates all operator trust (billing and infrastructure still exist).

## What you get

* **Two ways in** — **Log in with wallet** (Leviathan extension) or **Get started** (`lev_` API key).
* **Prepaid credits** — each successful chat completion costs **1 credit**. New accounts start at **0**.
* **Open-weight catalog** — default model is `qwen3.8-27b`. The UI lists the live catalog. `gpt-oss-120b` is no longer served. See [Models](model.md).
* **Attestable TEEs** — gateway attestation is a public surface; model-node attestation is documented for builders who verify with the FOSS toolkit.
* **E2EE (ACI v2)** — the hosted chat UI encrypts prompts to the attested enclave keyset so the Edge relays ciphertext only. See [Chat UI](chat-ui.md).
* **Per-key receipts** — successful chats return an `x-receipt-id`; receipts are private to the key that created them.

## Architecture (testnet)

```mermaid
sequenceDiagram
  participant UI as Chat UI / client
  participant Edge as Metering Edge
  participant Auth as Auth service
  participant GW as TDX gateway TEE
  participant Model as GPU-TEE model node

  UI->>Auth: Signup or wallet session / buy credits
  Auth-->>UI: lev_ key or wallet session / checkout or on-chain order
  UI->>GW: Attestation report (public)
  UI->>UI: Seal prompt (E2EE v2)
  UI->>Edge: Bearer lev_ + ciphertext chat
  Edge->>GW: Forward (cannot read plaintext under E2EE)
  GW->>Model: Inference inside GPU-TEE
  Model-->>GW: Completion
  GW-->>UI: Ciphertext reply + receipt id
  UI->>UI: Unseal reply locally
```

| Component | Testnet URL / role |
|-----------|--------------------|
| Chat UI | [ai-tee-leviathan.up.railway.app](https://ai-tee-leviathan.up.railway.app/) |
| Edge (gateway front) | `https://leviathan-edge.duckdns.org` |
| Auth (signup, credits, validate) | `https://leviathan-auth.duckdns.org` |
| Default model | `qwen3.8-27b` |

The UI talks to Edge and Auth through a **same-origin proxy** on the UI host (`/gw`, `/auth`) so browsers do not need CORS on those services.

## Trust boundaries (honest)

**What TEEs + E2EE are for**

* Processing prompts in CPU-encrypted / GPU-confidential memory rather than an ordinary host process you cannot measure.
* Giving you (or a verifier) cryptographic evidence about enclave composition.
* Keeping plaintext off the metering Edge when E2EE is applied (`x-e2ee-applied: true`).

**What they are not**

* Not a substitute for careful key backup. The auth service stores only the **SHA-256 hash** of an API key and cannot re-show the secret.
* Not free unlimited inference. Credits are prepaid; unpaid chats return HTTP `402`.
* Not a claim that operators disappear. Auth, Edge, and payment infrastructure are still operated.

## Start here

1. [Open Private AI](https://ai-tee-leviathan.up.railway.app/) — or read the [chat UI](chat-ui.md) guide.
2. [Buy credits](credits.md) — wallet or Stripe sandbox card.
3. [Models](model.md) — default `qwen3.8-27b`.
4. [Verify Confidential AI](verify.md) — optional builder path to check attestation and E2EE yourself.
