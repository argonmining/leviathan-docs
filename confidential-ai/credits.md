# Credits (testnet)

Confidential AI uses **prepaid credits**. Credits are **not** on-chain WXNT/XNT. They meter chat usage.

Open the app: [https://ai-tee-leviathan.up.railway.app/](https://ai-tee-leviathan.up.railway.app/)

## Rules

| Rule | Detail |
|------|--------|
| Starting balance | New accounts start at **0** credits |
| Chat cost | **1 credit** per successful chat completion |
| Unfunded chats | HTTP **402** until you top up |
| Default pack | **300 credits** |

## How to buy credits

1. Open [Private AI](https://ai-tee-leviathan.up.railway.app/) and log in (wallet or **Get started**).
2. Click **Buy 300 credits**.

**Wallet** (default when you logged in with the extension):

* Approve one transaction in the Leviathan wallet.
* Wait about **90 seconds** for proving and the next block. The balance updates in the same tab.
* Pressing the button again during that wait does not pay twice.
* This uses testnet tokens. Mint test USDT from the wallet faucet if the wallet has none.

**Card**:

* Opens Stripe sandbox checkout.
* Test card `4242 4242 4242 4242`, any future expiry and CVC.
* Return to the chat tab and **Refresh balance**.

Do not send real mainnet funds for testnet credits.

You can confirm an order by memo (example shape: `intent-…`):

```bash
curl -sS "https://leviathan-auth.duckdns.org/v1/payment-intents/<memo>"
```

A paid response has `"status": "paid"`.

## Read next

* [Chat UI](chat-ui.md)
* [Confidential AI overview](overview.md)
* [Verify Confidential AI](verify.md)
