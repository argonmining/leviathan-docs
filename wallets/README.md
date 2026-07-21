# Wallets on Leviathan testnet

Pioneers use wallets on the **programmable layer** (Miden accounts, WXNT, notes). Leviathan testnet is **not** mainnet. Assets have no real-world value.

## Recommended: Leviathan Chrome extension

The **Leviathan Chrome extension** is the primary pioneer wallet. It is distributed as a **developer (Load unpacked)** package through the **Leviathan Pioneers Telegram group** (see the pinned message). It is **not** on the Chrome Web Store, and the wallet repository is **not** public.

See [Install the Chrome extension](chrome-extension.md).

## Also available: hosted web wallet

The explorer hosts a browser wallet at [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet). It remains a documented option for pioneers who prefer a tab-only setup. The Chrome extension is the product target for ongoing pioneer UX.

See [Hosted web wallet](web-wallet.md).

## Not covered here

* **iOS / Android** builds — internal only; not part of the public pioneer docs.
* **Desktop (Tauri)** — not documented as a pioneer distribution path on this page.
* **DEX** — still [coming soon](../coming-soon/README.md).

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
