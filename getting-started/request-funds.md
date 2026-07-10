# Request testnet funds

Testnet WXNT is not available from a public self-serve faucet in the wallet UI. Pioneers receive funds by sharing a wallet address with the team.

## What to send the team

After [creating a wallet](create-wallet.md), copy your **Account ID** (hex format, shown on the account card) and send it through your pioneer channel (Telegram, Discord, or whatever channel the team gave you).

Example format:

```
Account ID: 9b2994fe7348f1100d2eb761f4c5f0
```

You can request funds for multiple account IDs if you are testing sends between wallets.

## What happens next

A team operator mints WXNT to your account on testnet. This is a manual step on our side, not something you trigger from the wallet.

After funding:

1. Open [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet)
2. Click **Connect Wallet**
3. Click **Sync**
4. Check your account card for a WXNT balance

If you see **claimable** notes on the account, click **Consume** to claim them into your balance.

## WXNT Faucet ID (reference)

When sending tokens yourself or verifying balances, the testnet WXNT faucet ID is:

```
b0682b76d8939720429ec7e43f194a
```

You may enter this in the **Faucet ID** field on the Send Tokens form. A `0x` prefix is optional depending on how the UI accepts input; use the hex string shown on your account card for account IDs.

## About the Mint Tokens panel

The wallet page includes a **Mint Tokens** section with Target Account, Faucet, and Amount fields. This panel is **operator tooling** and requires the faucet's private key. It is not available to regular pioneer users.

Do not expect self-serve minting to work unless you are running operator infrastructure. Use the request process above instead.

## Troubleshooting

| Issue | What to try |
|-------|-------------|
| Balance still zero after funding | Click **Sync**, then **Consume** if claimable notes appear |
| Wrong account funded | Double check the hex ID you sent matches the account card exactly |
| Account missing after browser update | Re-import using **Import ID** or your exported `.mac` file |

## Next step

Once you have a balance, try [sending tokens](send-tokens.md) between two of your accounts.
