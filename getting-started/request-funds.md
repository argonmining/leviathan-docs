# Get testnet funds

Leviathan testnet WXNT is for experimentation only. There is **no real-world value**.

## Preferred path: Faucet in the Chrome extension

Use the **Leviathan Chrome extension** ([install](../wallets/chrome-extension.md)).

1. Open the extension and finish wallet creation.
2. Open **Receive** and confirm you see a **bech32** address (`mtst1…`). You can leave this tab available for paste.
3. From home, open **Faucet** (action labeled **Faucet**).
4. On the **Leviathan Faucet** screen, read the short message, then click **Go to Faucet**.
5. The extension copies your receive address and opens the **faucet page configured in that pioneer build** in a browser view or tab.
6. Complete the faucet page using your address (paste if the page did not prefill). Follow that page’s own confirmation steps.
7. Return to the extension. **Sync**. If you see claimable notes, **Consume** them.
8. Confirm a WXNT (or other test asset) balance on home / account views.

### If the faucet page errors or balance stays zero

1. Sync again and check claimable notes.
2. Confirm you used the **same** account that the extension copied.
3. Use the [fallback](#fallback-ask-the-pioneers-team) below.
4. Ask in Pioneers Telegram whether the pinned build’s faucet endpoint was updated.

Do **not** paste seed phrases into any faucet page.

## Fallback: ask the Pioneers team

If self-serve faucet access is unavailable or stuck:

1. Copy your address from the extension **Receive** screen (bech32), or your account id from the [hosted web wallet](../wallets/web-wallet.md) (hex or bech32).
2. Send that address in the Pioneers Telegram channel (or the funding thread the team designates).
3. Wait for an operator mint.
4. **Sync** (and **Consume** if claimable) in the wallet you used.

Example message shape:

```text
Please fund this testnet account:
mtst1...your_bech32_address...
```

## WXNT faucet contract ID (reference)

When a send form asks for a **Faucet** / token id for WXNT, use:

```text
b0682b76d8939720429ec7e43f194a
```

This identifies the WXNT faucet contract on the programmable layer. It is not a substitute for the self-serve faucet UI, and it is not a private key.

## What not to use

* **Mint Tokens** on the hosted web wallet — operator-only; needs the faucet private key.
* Random third-party “faucets” or wallet downloads outside the Pioneers Telegram pin.
* Mainnet addresses or mainnet faucets — this stack is **testnet-locked** for pioneers.

## Troubleshooting

| Issue | What to try |
|-------|-------------|
| Balance still zero | Sync; Consume claimable notes; wait for inclusion; retry faucet or ask the team |
| Faucet opened but rejected address | Use bech32 from extension Receive; do not mix accounts |
| Web wallet send/fund field rejects input | Try the other format (hex vs bech32); copy-paste, do not retype |
| Wrong account funded | Compare the string you sent to Receive / account card character-for-character |

## Next step

[Send tokens](send-tokens.md) between accounts you control.
