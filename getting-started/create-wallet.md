# Create a wallet

The Leviathan testnet wallet runs entirely in your browser. No extension install is required for the current pioneer experience.

**Wallet URL:** [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet)

## Step 1: Connect

1. Open the wallet page.
2. Click **Connect Wallet** in the top right.
3. Wait a few seconds while the page loads the Miden WASM SDK. The button will change to show **Sync**, **Disconnect**, and **Clear** when ready.

Your keys and account data are stored locally in the browser (IndexedDB). Clearing site data or using a different browser means you need to import your account again.

## Step 2: Create an account

1. In the **Accounts** section, click **Create**.
2. A panel appears: **New Wallet Account** with the description *Public wallet with Falcon512 auth*.
3. Click **Create** in that panel.
4. Your new account appears in the list with a hexadecimal **Account ID**.

Copy the full account ID. You will need it to request testnet funds and to send tokens.

## Step 3: Sync

Click **Sync** in the header after creating an account or receiving funds. The dashboard shows:

* **Sync Height** — latest block the wallet has synced to
* **Accounts** — number of accounts in this browser session
* **Total Assets** — combined balance across accounts
* **Claimable** — notes waiting to be consumed

If you receive funds but do not see a balance, sync first. If you still see claimable notes, use **Consume** on the account card.

## Multiple wallets

You can create as many accounts as you want in the same browser session. This is useful for testing sends between your own addresses:

1. Create account A
2. Create account B
3. Request funds for account A (or both)
4. [Send tokens](send-tokens.md) from A to B

Each account has its own hex ID and nonce counter.

## Import an existing account

If you already have an account from another session or device:

**Import ID** — paste a hex Account ID to reattach an account this browser previously created (same browser storage) or to import by ID if supported.

**Import File** — drag and drop or browse for a `.mac` account file exported from this wallet.

**Export** — use **Export .mac** on an account card to back up an account before clearing browser data.

## Tips

* Use a desktop browser for the smoothest WASM experience.
* Write down or securely store account IDs you care about.
* The **Clear** button removes local wallet data. Export first if you need to keep an account.

## Next step

[Request testnet funds](request-funds.md) using your new Account ID.
