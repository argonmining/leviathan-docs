# Confidential AI chat UI

Hosted testnet UI for Leviathan Private AI:

**[https://ai-tee-leviathan.up.railway.app/](https://ai-tee-leviathan.up.railway.app/)**

<a href="https://ai-tee-leviathan.up.railway.app/" class="button primary">Open Private AI</a>

Use this for a browser chat with wallet or browser-account login, prepaid credits, **E2EE by default**, and local conversation history.

## What the UI does

| Capability | Behavior |
|------------|----------|
| Account | **Log in with wallet** (Leviathan extension) or **Get started** (stores a `lev_` key in IndexedDB) |
| Backup | API-key accounts: **Export backup** downloads a JSON file with the **API key only**. **Restore** imports that key |
| Credits | **Buy 300 credits**. Wallet rail pays from the connected account (about 90 seconds to credit). Card rail opens Stripe sandbox (`4242 4242 4242 4242`) |
| Chat | Each send fetches attestation, seals messages (ACI E2EE v2), posts to Edge, unseals the reply |
| Web search | Optional **Web** toggle. When on, the search queries leave the TEE and are shown under the reply |
| History | Conversations live in IndexedDB on **this browser only**. **Export PDF** saves the open thread |
| Theme | Light / dark toggle |
| Model | Toolbar picker. Default is `qwen3.8-27b`. See [Models](model.md) |

## Flow

1. Open [https://ai-tee-leviathan.up.railway.app/](https://ai-tee-leviathan.up.railway.app/).
2. **Log in with wallet**, or click **Get started**.
3. **Buy 300 credits** and wait until the balance updates.
4. Send a message. You should see your bubble immediately, then a short waiting state, then the assistant reply.
5. Receipt ids (when present) appear under assistant messages.

Each successful reply costs **1 credit**.

## Privacy model in the UI

* **Prompts / answers in transit:** encrypted to the attested enclave (E2EE).
* **Conversation text at rest:** stored in plaintext in **your browser’s IndexedDB**. Clearing site data or signing out removes it.
* **Sign out:** clears the local session and local conversation history for that browser profile.
* **Web search:** off by default. Turning it on sends those queries to a public search service.

## What the UI is not

* Not a Chrome Web Store product. The wallet extension is a [separate download](../wallets/chrome-extension.md).
* Not a place to paste raw `lev_` keys as the primary UX (use **Export / Restore**).
* Not a substitute for [attestation verification](verify.md) if you need cryptographic proof beyond “the UI worked.”

## Read next

* [Credits](credits.md)
* [Models](model.md)
* [Confidential AI overview](overview.md)
