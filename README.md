# Leviathan Documentation

Official documentation for **Leviathan**, the privacy and programmability stack built on Neptune and Miden.

> **Status:** Public testnet. Testnet assets have **no real-world value**. This documentation describes the public experience on [leviathandev.neptune.io](https://leviathandev.neptune.io).

<a href="https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-07-17/leviathan-chrome-testnet.zip" class="button primary">Download Chrome extension</a>
<a href="https://ai-tee-leviathan.up.railway.app/" class="button secondary">Open Private AI</a>

## Quick links

| Resource | URL |
|----------|-----|
| Explorer | [leviathandev.neptune.io](https://leviathandev.neptune.io/) |
| Hosted web wallet | [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet) |
| Bridge monitor | [leviathandev.neptune.io/bridge](https://leviathandev.neptune.io/bridge) |
| Private AI (TEE chat) | [ai-tee-leviathan.up.railway.app](https://ai-tee-leviathan.up.railway.app/) |
| NeptuneSwap (DEX) | [testnet.zkswap.ai](https://testnet.zkswap.ai/) |
| Chrome extension (v1.14.0) | [leviathan-chrome-testnet.zip](https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-07-17/leviathan-chrome-testnet.zip) |
| WXNT Faucet ID | `b0682b76d8939720429ec7e43f194a` |

## What is Leviathan?

Leviathan combines a **privacy focused base layer** (Neptune, native asset XNT) with a **programmable layer** (Miden, wrapped asset WXNT) connected by a cryptographic bridge. Proofs, not trust, secure value movement between layers.

## Start here

1. [Install the Leviathan Chrome extension](wallets/chrome-extension.md) — [download v1.14.0](https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-07-17/leviathan-chrome-testnet.zip)
2. [Request testnet funds](getting-started/request-funds.md)
3. [Send tokens](getting-started/send-tokens.md)
4. [Chat with Private AI](https://ai-tee-leviathan.up.railway.app/) — open-weight models inside attested TEEs

Hosted web wallet docs: [wallets/web-wallet.md](wallets/web-wallet.md). DEX: [NeptuneSwap](dex/overview.md) at [testnet.zkswap.ai](https://testnet.zkswap.ai/).

## TEE proving (testnet)

Heavy STARK proving can be **delegated** to an attested enclave (Intel TDX on Phala) so builders do not need to run every proof locally. Start here:

* [TEE proving overview](tee/overview.md)
* [Attestation and trust](tee/attestation.md)
* [Set up delegated TEE proving](tee/setup.md)
* [TEE proving FAQ](tee/faq.md)

## Private AI (testnet)

Chat with open-weight models inside attested TEEs. Prompts are end-to-end encrypted. Log in with the Leviathan wallet or a browser account, then buy credits with the wallet or a Stripe sandbox card.

**Open the app:** [https://ai-tee-leviathan.up.railway.app/](https://ai-tee-leviathan.up.railway.app/)

* [Confidential AI overview](confidential-ai/overview.md)
* [Models](confidential-ai/model.md) — default `qwen3.8-27b`, picker in the UI
* [Credits](confidential-ai/credits.md)
* [Chat UI](confidential-ai/chat-ui.md)
* [Verify Confidential AI](confidential-ai/verify.md)
