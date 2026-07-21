# Install the Leviathan Chrome extension

The **Leviathan** Chrome extension is the primary pioneer wallet for Leviathan testnet. Builds are shared with **Leviathan Pioneers** members. There is no public Chrome Web Store listing and no public git checkout for end users.

## Before you start

* Google Chrome (or a Chromium browser that supports unpacked extensions)
* Membership in the **Leviathan Pioneers Telegram group**
* Willingness to use **Developer mode** / **Load unpacked** (this is intentional for the closed beta)

The extension is built for **testnet**. Treat every balance as worthless test assets.

## Step 1 — Get the package from Pioneers Telegram

1. Open the Leviathan Pioneers Telegram group.
2. Open the **pinned** message that links the current Chrome extension package (zip or folder instructions).
3. Download that package to your computer.
4. If it is a zip file, **fully unzip** it. Chrome must load a folder that contains `manifest.json`, not the zip itself.

If you do not see a pin or the link expired, ask in the group. Do not download “Leviathan” wallets from random third parties.

## Step 2 — Load unpacked in Chrome

1. Open `chrome://extensions` in Chrome.
2. Turn on **Developer mode** (top right).
3. Click **Load unpacked**.
4. Select the unzipped extension folder (the directory that contains `manifest.json`).
5. Confirm an extension named **Leviathan** appears in the list.
6. Pin it from the puzzle-piece extensions menu for easier access.

To update later: remove the old unpacked extension (or replace files and click **Reload** on `chrome://extensions`), then load the new package from the latest pin.

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

From home you can open flows such as **Send**, **Receive**, and **Faucet** (see [Get testnet funds](../getting-started/request-funds.md)).

## Network note

Pioneer builds default to **Testnet**. The header network control may be disabled in the UI. Do not expect mainnet balances or mainnet addresses to work in this build.

## Security checklist

* Never share your seed phrase or password in Telegram.
* Prefer the pinned package from the official Pioneers group only.
* Uninstall old unpacked builds when you switch to a new zip so you do not run two conflicting versions.
* Export or back up accounts before clearing extension data.

## Related

* [Wallets overview](README.md)
* [Get testnet funds](../getting-started/request-funds.md)
* [Send tokens](../getting-started/send-tokens.md)
* [Hosted web wallet](web-wallet.md) (secondary option)
