# Wallets on Leviathan testnet

Pioneers and public testers use wallets on the **programmable layer** (Miden accounts, WXNT, notes). Leviathan testnet is **not** mainnet. Assets have no real-world value.

## Recommended: Leviathan Chrome extension

The **Leviathan Chrome extension** is the primary wallet. Download the official zip and load it unpacked. It is **not** on the Chrome Web Store yet.

[Download v1.14.0](https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-07-17/leviathan-chrome-testnet.zip) · [Install steps](chrome-extension.md)

## Also available: hosted web wallet

The explorer hosts a browser wallet at [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet). It remains a documented option if you cannot install the extension. The Chrome extension is the product target.

See [Hosted web wallet](web-wallet.md).

## Not covered here

* **iOS / Android** builds — internal only; not part of the public pioneer docs.
* **Desktop (Tauri)** — not documented as a pioneer distribution path on this page.
* **DEX** — use **[NeptuneSwap](../dex/overview.md)** at [testnet.zkswap.ai](https://testnet.zkswap.ai/) (connect Leviathan Wallet).

## Address formats (important)

| Surface | Receive address shown | What to paste when sending / funding |
|---------|----------------------|--------------------------------------|
| Chrome extension | **bech32** only (for example `mtst1…`) | bech32 (`mtst1…`) |
| Hosted web wallet | Account ID on the account card | **hex or bech32** accepted |

If a tool only understands hex and you only have bech32 from the extension, use the hosted wallet’s dual-format fields where applicable, or ask in the Pioneers channel. Do not invent conversions from chat screenshots.

## Next steps

1. [Install the Chrome extension](chrome-extension.md)
2. [Request testnet funds](../getting-started/request-funds.md)
3. [Send tokens](../getting-started/send-tokens.md)
