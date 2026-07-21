# Hosted web wallet

The hosted wallet at [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet) runs in a browser tab. It is a supported pioneer option. The **Leviathan Chrome extension** remains the primary product path ([install guide](chrome-extension.md)).

## Create an account

1. Open [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet).
2. Click **Connect Wallet**. Wait until **Sync**, **Disconnect**, and **Clear** appear (WASM load).
3. Under **Accounts**, click **Create**.
4. Confirm **New Wallet Account** / public wallet with Falcon512 auth, then **Create**.
5. Copy the account identifier from the account card.

Keys and account data live in the browser (IndexedDB). Clearing site data removes local wallet state unless you exported a `.mac` file.

## Address formats on the web wallet

The hosted wallet accepts **hex Account IDs and bech32 addresses** in the flows that take an account target (for example send / funding-related fields, depending on the deployed UI). Prefer copying directly from the account card or from the Chrome extension Receive screen rather than retyping.

## Sync and claimable notes

Click **Sync** after create, fund, or receive. If the account shows **claimable** notes, use **Consume** so WXNT becomes a spendable balance.

## Import / export

* **Import ID** / **Import File** — restore from hex ID or `.mac` when the UI offers those controls.
* **Export .mac** — back up before **Clear** or browser resets.

## Mint Tokens panel (operators only)

The wallet page may show **Mint Tokens** (Target Account, Faucet, Amount, **Mint**). That panel is **operator tooling**. It requires the faucet private key. Regular pioneers should not expect it to work. Use [Get testnet funds](../getting-started/request-funds.md) instead.

## Related

* [Wallets overview](README.md)
* [Install the Chrome extension](chrome-extension.md)
* [Get testnet funds](../getting-started/request-funds.md)
* [Send tokens](../getting-started/send-tokens.md)
