# Request testnet funds

Testnet WXNT has **no real-world value**. Pioneers receive funds by joining the **Leviathan Pioneers** Telegram group and asking the team to mint to their address.

There is no public self-serve faucet in the pioneer docs. Ignore in-app **Faucet** buttons unless the team explicitly tells you to use a different process.

## Step 1 — Join Leviathan Pioneers

1. Join the **Leviathan Pioneers** Telegram group (invite from the team / announcement channels).
2. Use that group for extension packages (pinned message) and funding requests.

## Step 2 — Copy your address

**Chrome extension (recommended):**

1. Open **Receive**.
2. Copy the **bech32** address (`mtst1…`).

**Hosted web wallet (secondary):**

1. Open [leviathandev.neptune.io/wallet](https://leviathandev.neptune.io/wallet), connect, and open your account card.
2. Copy the account identifier. The hosted wallet accepts **hex or bech32** in relevant fields; either form is fine when messaging the team if you copy it exactly.

Never send your seed phrase or password.

## Step 3 — Request funds in Telegram

Post in the Pioneers group (or the funding thread the team designates), for example:

```text
Please fund this testnet account:
mtst1...your_bech32_address...
```

You can request funds for more than one account if you are testing sends between wallets.

## Step 4 — Sync and consume

After an operator mints:

1. Open the same wallet you funded.
2. **Sync**.
3. If you see **claimable** notes, **Consume** them.
4. Confirm a spendable balance.

## WXNT faucet contract ID (reference)

When a **Send** form asks for a token **Faucet** field for WXNT, use:

```text
b0682b76d8939720429ec7e43f194a
```

That is the on-chain faucet **contract** id used when specifying which asset to send. It is not a funding URL and not a private key.

## What not to use

* **Mint Tokens** on the hosted web wallet — operator tooling; requires the faucet private key.
* Random third-party faucets or wallet downloads outside the Pioneers Telegram pin.
* Mainnet addresses — pioneer wallets are **testnet**.

## Troubleshooting

| Issue | What to try |
|-------|-------------|
| Balance still zero | Wait for the operator reply; Sync; Consume claimable notes |
| Wrong account funded | Compare the string you posted to Receive / account card exactly |
| Extension vs web mismatch | Fund the wallet you will actually use; addresses differ by account |

## Next step

[Send tokens](send-tokens.md) between accounts you control.
