# Send tokens

Send WXNT (or other test assets) between accounts on the programmable layer. Prefer the **Leviathan Chrome extension**. The hosted web wallet remains available as a secondary path.

## Chrome extension (recommended)

### Before you send

1. Install and unlock the [Chrome extension](../wallets/chrome-extension.md).
2. Confirm the sender account has a spendable balance (Sync; Consume claimable notes if needed).
3. Have the recipient **bech32** address ready (`mtst1…`). Extension **Send** validation expects bech32-style Miden addresses (for example `mtst1`, not hex).

### Steps

1. Open **Send** from the extension.
2. Choose the token / amount.
3. Paste the recipient **bech32** address.
4. Review and confirm the transaction.
5. Wait for proving and submission to finish (local proving on the pioneer testnet build can take a while).
6. **Sync** on the recipient wallet. Consume claimable notes if shown.

### Testing between two accounts

1. Create wallet A and wallet B in the extension (or a second browser profile / second install — avoid mixing seeds).
2. Fund wallet A via [Request testnet funds](request-funds.md).
3. Copy B’s address from **Receive**.
4. Send from A to B.
5. Sync and consume on B.

## Hosted web wallet (secondary)

**Wallet URL:** [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet)

### Before you send

1. **Connect Wallet** and **Sync**.
2. Confirm spendable WXNT (consume claimable notes first if needed).
3. Recipient may be entered as **hex or bech32** on the hosted wallet.

### Send Tokens form fields

| Field | Description |
|-------|-------------|
| **Sender** | Sending account |
| **Recipient** | Destination account (hex or bech32) |
| **Faucet** | Token faucet ID — for WXNT use `b0682b76d8939720429ec7e43f194a` |
| **Amount** | Amount to send |

### Steps

1. Open the wallet and connect.
2. Use **Send Tokens**.
3. Fill Sender, Recipient, Faucet, and Amount.
4. Click **Send**.
5. Wait for the transaction ID.
6. **Sync** sender and recipient views.

## Explorer verification

1. Open [leviathandev.neptune.io](https://leviathandev.neptune.io/).
2. Search by transaction ID or account identifier.
3. Browse **Transactions** if needed.

## Burn WXNT (advanced)

The hosted wallet may include **Burn WXNT** for L1 withdrawal experiments. That path is more involved and still maturing. Most pioneers should stick to fund and send on the programmable layer first. See the [bridge monitor](../bridge/README.md).

## Related

* [Request testnet funds](request-funds.md)
* [Wallets overview](../wallets/README.md)
* [Testnet constants](../reference/testnet-constants.md)
