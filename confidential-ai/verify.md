# Verify Confidential AI

The chat UI is the convenience path. **Verification is optional** and intended for builders who want checkable evidence rather than trusting the hosted page alone.

Leviathan publishes a FOSS verify toolkit (separate repository) with scripts that exercise attestation, receipts, GPU-TEE evidence, and E2EE. The toolkit targets the same testnet endpoints the UI uses.

## Endpoints

```text
GATEWAY_URL  https://leviathan-edge.duckdns.org
AUTH_URL     https://leviathan-auth.duckdns.org
MODEL        gpt-oss-120b
```

## What you can prove

| Claim | Script (toolkit) | Notes |
|-------|------------------|-------|
| Gateway is a genuine Intel TDX TEE | `verify_gateway.py` | No API key required; attestation report is public |
| Exact request/answer committed in a signed, key-private receipt | `verify_response.py` | Uses your `lev_` key; costs a credit for the live chat path |
| Model upstream is TDX + NVIDIA GPU-TEE | `verify_model.py` | Needs an **operator** provider key (`TEE_AI_API_KEY`) |
| Edge cannot read prompt plaintext under E2EE | `verify_e2ee.py` / `example_e2ee_chat.py` | Matches the crypto the chat UI implements (ACI v2) |

Local hardware quote checks typically need a running `dstack-verifier` (Docker) pointed at by `DSTACK_VERIFIER_URL`.

## Minimal self-serve loop (no UI)

```bash
python signup.py
export API_KEY="lev_..."          # shown once

API_KEY=$API_KEY python buy_credits.py 300   # sandbox checkout

python example_e2ee_chat.py "your prompt"
```

## Relationship to the chat UI

* The UI already performs E2EE chat against the same Edge.
* Running verify scripts is how you **independently** check TDX quotes, receipt signatures, and ciphertext properties.
* UI success alone is not a formal attestation audit.

Obtain the toolkit from the team’s published verify repository / release notes for pioneers. Keep API keys and backup JSON files out of public channels.

## Read next

* [Confidential AI overview](overview.md)
* [Chat UI](chat-ui.md)
* [Credits and NOWPayments](credits.md)
* [TEE proving attestation](../tee/attestation.md) — related vocabulary for a different TEE workload (STARK proving)
