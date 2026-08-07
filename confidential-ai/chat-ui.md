# Confidential AI chat UI

Hosted testnet UI for Leviathan Confidential AI:

**[https://ai-tee-leviathan.up.railway.app/](https://ai-tee-leviathan.up.railway.app/)**

Use this when you want a browser chat experience with self-serve signup, NOWPayments credits, **E2EE by default**, and local conversation history — without running the Python verify toolkit.

## What the UI does

| Capability | Behavior |
|------------|----------|
| Account | **Get started** calls Auth signup and stores the `lev_` key in **IndexedDB** (not shown in the UI after creation) |
| Backup | **Export backup** downloads a JSON file containing the key; **Restore** on the gate imports it |
| Credits | **Buy credits** opens NOWPayments; **Refresh balance** re-reads Auth |
| Chat | Each send fetches attestation, seals messages (ACI E2EE v2), posts to Edge, unseals the reply |
| History | Conversations live in IndexedDB on **this browser only** |
| Theme | Light / dark toggle (persisted in `localStorage`) |
| Model | `gpt-oss-120b` (see [The model](model.md)) |

## Pioneer flow

1. Open the UI URL above.
2. Click **Get started**. Wait for the account to be created and saved locally.
3. Optional but recommended: **Export backup** and store the file privately.
4. **Buy credits** and complete the [sandbox checkout](credits.md) (do not send real funds).
5. **Refresh balance** until credits appear (for example `300`).
6. Send a message. You should see your bubble immediately, then a short “waiting on TEE” state, then the assistant reply.
7. Receipt ids (when present) appear under assistant messages.

Each successful reply costs **1 credit**.

## Privacy model in the UI

* **Prompts / answers in transit:** encrypted to the attested enclave (E2EE). The UI refuses to accept a reply if `x-e2ee-applied` is not `true`.
* **Conversation text at rest:** stored in plaintext in **your browser’s IndexedDB** so the thread can render. Clearing site data or signing out removes it.
* **Sign out:** clears the local session **and** local conversation history for that browser profile.
* **Restore backup:** restores the API key only — it does **not** restore deleted chat history unless you still have it in that browser’s IndexedDB.

This is intentional for a lightweight testnet client. It is not a full encrypted-at-rest messaging product.

## What the UI is not

* Not Chrome extension / wallet login.
* Not a place to paste raw `lev_` keys as the primary UX (use **Export / Restore** instead).
* Not a multi-model switcher.
* Not a substitute for [attestation verification](verify.md) if you need cryptographic proof beyond “the UI worked.”

## Operator notes (deploy)

The UI is a small Vite + Express app. In production it serves static assets and proxies:

* `/gw` → `EDGE_URL` (default `https://leviathan-edge.duckdns.org`)
* `/auth` → `AUTH_URL` (default `https://leviathan-auth.duckdns.org`)

Optional env: `MODEL`, `EDGE_URL`, `AUTH_URL`. Railway sets `PORT`.

## Read next

* [Credits and NOWPayments](credits.md)
* [The model](model.md)
* [Confidential AI overview](overview.md)
