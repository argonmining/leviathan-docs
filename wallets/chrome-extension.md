# Install the Leviathan Chrome extension

The **Leviathan** Chrome extension is the wallet for Leviathan public testnet. There is no Chrome Web Store listing yet. Install the official zip with **Load unpacked**.

<a href="https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-09-29/leviathan-chrome-testnet.zip" class="button primary">Download Leviathan Chrome v1.14.0</a>

## Before you start

* Google Chrome (or a Chromium browser that supports unpacked extensions)
* Willingness to use **Developer mode** / **Load unpacked**

The extension is built for **testnet**. Treat every balance as worthless test assets. Download only the zip linked on this page.

## Step 1 — Download the package

1. Download [leviathan-chrome-testnet.zip](https://github.com/argonmining/leviathan-docs/releases/download/chrome-v1.14.0-2026-09-29/leviathan-chrome-testnet.zip) (v1.14.0, build `9af28d25`).
2. **Fully unzip** it. Open the **`leviathan`** folder. That folder contains `manifest.json`. Chrome must load that folder, not the zip.

Do not install “Leviathan” wallets from random third parties. The release page is [chrome-v1.14.0-2026-09-29](https://github.com/argonmining/leviathan-docs/releases/tag/chrome-v1.14.0-2026-09-29).

## Step 2 — Load unpacked in Chrome

1. Open `chrome://extensions` in Chrome.
2. Turn on **Developer mode** (top right).
3. Click **Load unpacked**.
4. Select the unzipped **`leviathan`** folder (the directory that contains `manifest.json`).
5. Confirm an extension named **Leviathan** appears in the list.
6. Pin it from the puzzle-piece extensions menu for easier access.

To update later: remove the old unpacked extension (or replace files and click **Reload** on `chrome://extensions`), then load the folder from the latest zip on this page.

## Step 3 — Create a wallet

Open the extension popup (or full page, depending on how the build opens).

Typical create path:

1. Choose **Create a new wallet** (not import).
2. **Backup** the seed phrase offline. Anyone with the phrase controls the account.
3. **Verify** the seed phrase when prompted.
4. Set a password if the build asks for one.
5. Wait for **confirmation** / account creation to finish.

Import paths (“I already have a wallet”) exist for seed or file import; use them only if you already have a Leviathan account backup.

## Step 4 — Copy your receive address

Open **Receive**. The extension shows a **bech32** address (testnet prefixes such as `mtst1…`). That is the address you use for funding and for receiving from other extension users.

The Receive screen does **not** show a hex Account ID. Keep the bech32 string exactly as displayed when you request funds or paste into a send form that accepts bech32.

## Step 5 — Sync and use the home screen

Use **Sync** (or wait for automatic sync if enabled) after funding or receiving notes. If the UI shows claimable notes, **consume** them so balances become spendable.

From home you can open flows such as **Send** and **Receive**. For funding, see [Request testnet funds](../getting-started/request-funds.md). For swaps, connect this extension to [NeptuneSwap](../dex/overview.md) and always **Sync** → **Consume** after a trade.

## Network note

Public testnet builds default to **Testnet**. Do not expect mainnet balances or mainnet addresses to work in this build.

## Security checklist

* Never share your seed phrase or password.
* Install only the zip linked from this documentation.
* Uninstall old unpacked builds when you switch to a new zip so you do not run two conflicting versions.
* Export or back up accounts before clearing extension data.

## Related

* [Wallets overview](README.md)
* [Request testnet funds](../getting-started/request-funds.md)
* [Send tokens](../getting-started/send-tokens.md)
* [Hosted web wallet](web-wallet.md) (secondary option)
