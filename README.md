# Leviathan Documentation

Official documentation for **Leviathan**, the privacy and programmability stack built on Neptune and Miden.

> **Status:** Testnet only. This documentation describes the current developer and pioneer experience on [leviathandev.neptune.io](https://leviathandev.neptune.io). Features and interfaces may change as we iterate.

## Quick links

| Resource | URL |
|----------|-----|
| Explorer | [leviathandev.neptune.io](https://leviathandev.neptune.io/) |
| Hosted web wallet | [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet) |
| Bridge monitor | [leviathandev.neptune.io/bridge](https://leviathandev.neptune.io/bridge) |
| Chrome extension | Pioneers Telegram (pinned package — Load unpacked) |
| WXNT Faucet ID | `b0682b76d8939720429ec7e43f194a` |

## What is Leviathan?

Leviathan combines a **privacy focused base layer** (Neptune, native asset XNT) with a **programmable layer** (Miden, wrapped asset WXNT) connected by a cryptographic bridge. Proofs, not trust, secure value movement between layers.

## Start here (pioneers)

1. [Install the Leviathan Chrome extension](wallets/chrome-extension.md)
2. [Get testnet funds](getting-started/request-funds.md)
3. [Send tokens](getting-started/send-tokens.md)

Hosted web wallet docs: [wallets/web-wallet.md](wallets/web-wallet.md). DEX: still [coming soon](coming-soon/README.md).

## TEE proving (testnet)

Heavy STARK proving can be **delegated** to an attested enclave (Intel TDX on Phala) so builders do not need to run every proof locally. Start here:

* [TEE proving overview](tee/overview.md)
* [Attestation and trust](tee/attestation.md)
* [Set up delegated TEE proving](tee/setup.md)
* [TEE proving FAQ](tee/faq.md)
