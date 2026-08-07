# Credits and NOWPayments (testnet)

Confidential AI uses **prepaid credits** managed by the auth service. Credits are **not** on-chain WXNT/XNT. They meter API usage for the Edge / gateway.

## Rules (current testnet)

| Rule | Detail |
|------|--------|
| Signup balance | New `lev_` keys start at **0** credits |
| Chat cost | **1 credit** per successful chat completion |
| Unfunded chats | HTTP **402** until you top up |
| Binding | Payment intents are bound to **your** key’s identity at creation; a checkout URL cannot credit a different account |
| Key storage | Auth stores only `sha256(api_key)` — it cannot recover a lost plaintext key |

## How to buy credits

### From the chat UI (recommended)

1. Open [Confidential AI chat](https://ai-tee-leviathan.up.railway.app/) and complete [Get started](chat-ui.md) (or restore a backup).
2. Click **Buy credits**.
3. A NOWPayments checkout opens in a new tab (default purchase: **300 credits** ≈ **$3.00** USD on the current intent pricing).
4. Complete the **sandbox** flow below.
5. Return to the UI and click **Refresh balance**.

### From the FOSS scripts

```bash
export AUTH_URL="https://leviathan-auth.duckdns.org"
export API_KEY="lev_..."   # your key

API_KEY=$API_KEY python buy_credits.py 300
```

The script creates a payment intent, opens checkout, and polls until status is `paid`.

## NOWPayments sandbox process (important)

Testnet billing is wired to **NOWPayments sandbox** behavior. You should **not** send real mainnet crypto.

### Steps that work today

1. On the checkout page, open **1. Choose asset**.
2. Prefer a stablecoin option such as **USDT** (network may show BSC, ETH, etc. depending on the invoice).
3. Click **Next step >**.
4. You will see a deposit address / QR and a status of **Waiting for payment**.
5. **Do not send funds.** Wait roughly **60 seconds** (sometimes a bit longer).
6. Auth should mark the intent `paid` and credit your balance even if the NOWPayments page still shows “Waiting.”
7. In the chat UI, click **Refresh balance**.

You can confirm an order by memo (example shape: `intent-…`):

```bash
curl -sS "https://leviathan-auth.duckdns.org/v1/payment-intents/<memo>"
```

A paid response looks like:

```json
{
  "memo": "intent-…",
  "status": "paid",
  "credits": 300,
  "amount_cents": 300
}
```

### What “sandbox” means in practice

* Checkout UI can look like a live deposit page (address, timer, amount). That does **not** mean you must pay with real assets on testnet.
* Credits land when the **auth service** accepts the provider webhook / sandbox completion — not when you manually transfer coins.
* If balance stays at `0` after several minutes, the NOWPayments mode or webhook config may not be sandbox; escalate to whoever operates Auth. Do not “fix” it by sending real money unless you intentionally mean to.

## Credential types (avoid a common 401)

| Value | Send to | Field |
|-------|---------|--------|
| Raw `api_key` (`lev_…`) | Edge / gateway | `Authorization: Bearer …` |
| `sha256(api_key)` hex | Auth | `credential_value` with `credential_type: "api_key"` |

Buying credits and validating balance use the **hash**. Chatting uses the **raw key**.

## Rotating keys

If you still hold a live key, you can rotate with the FOSS `rotate_key.py` helper: identity, credits, and receipts stay with the account; a new `lev_` secret is issued once. The chat UI’s **Export backup** should be refreshed after rotation.

## Read next

* [Chat UI](chat-ui.md)
* [Confidential AI overview](overview.md)
* [Verify Confidential AI](verify.md)
