# Send tokens

Once your account holds WXNT, you can transfer between accounts on the programmable layer using the wallet's **Send Tokens** panel.

**Wallet URL:** [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet)

## Before you send

1. Connect your wallet and sync.
2. Confirm the sender account shows a WXNT balance (not just claimable notes — consume first if needed).
3. Have the recipient **Account ID** ready (hex). If testing yourself, create a second account and copy its ID.

## Send form fields

| Field | Description |
|-------|-------------|
| **Sender** | Hex Account ID of the account sending WXNT |
| **Recipient** | Hex Account ID of the receiving account |
| **Faucet** | Token faucet ID — use `b0682b76d8939720429ec7e43f194a` for WXNT |
| **Amount** | Whole number of WXNT units to send |

## Steps

1. Open the wallet and connect.
2. Scroll to **Send Tokens** in the right sidebar.
3. Fill in Sender, Recipient, Faucet, and Amount.
4. Click **Send**.
5. Wait for the transaction to complete. A transaction ID appears in the status area when successful.
6. Click **Sync** on both accounts (or refresh the recipient in a second browser profile) to see updated balances.

## Testing between two accounts

A simple pioneer exercise:

1. Create **Wallet A** and **Wallet B**
2. Request funds for **Wallet A** only
3. Send half the balance from A to B
4. Sync and confirm both account cards update

## Explorer verification

After sending, you can look up the transaction on the explorer:

1. Go to [leviathandev.neptune.io](https://leviathandev.neptune.io/)
2. Use the search bar or browse **Transactions**
3. Search by transaction ID or account ID

## Burn WXNT (advanced)

The wallet also includes a **Burn WXNT** panel for withdrawing to Neptune L1. This path is more involved (requires a Neptune L1 receiving address in bech32m format, minimum 1 WXNT) and is still maturing on testnet. Most pioneers should focus on create, fund, and send first.

Details: *Burn WXNT to withdraw XNT on Neptune L1. 1 WXNT = 1 XNT. Min 1 WXNT.*

Bridge settlement timing and L1 wallet setup are documented separately as those flows stabilize.
