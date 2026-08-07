# The model (`gpt-oss-120b`)

Confidential AI on Leviathan testnet serves a single model id:

```text
gpt-oss-120b
```

That string is what clients send in OpenAI-compatible `model` fields (chat completions) and what E2EE AAD binds to for each exchange. The hosted [chat UI](chat-ui.md) uses this id by default (overridable only via the UI service’s `MODEL` environment variable if operators change the deployment).

## What “FOSS” means here

`gpt-oss-120b` is part of OpenAI’s **gpt-oss** open-weight series:

* **License:** Apache 2.0 (permissive open weights — not a closed proprietary API-only model).
* **Weights:** published for download (for example on [Hugging Face: `openai/gpt-oss-120b`](https://huggingface.co/openai/gpt-oss-120b)).
* **Shape:** mixture-of-experts style open-weight model; public materials describe on the order of **117B total parameters** with roughly **5.1B active** per token, designed to fit a single large GPU class machine under MXFP4 quantization.

“Open-weight / Apache 2.0” means you can inspect and redistribute the **weights** under that license. It does **not** mean Leviathan’s hosted inference stack, Edge, or Auth code are all the same license, and it does not mean every GPU kernel or orchestration component is independently audited by you unless you verify those layers yourself.

## How Leviathan runs it (testnet)

| Layer | Role |
|-------|------|
| **Model node** | Serves `gpt-oss-120b` inside an **NVIDIA GPU-TEE** (with Intel TDX evidence on the confidential upstream). This is the inference TEE. |
| **Gateway TEE** | Intel **TDX** enclave that handles attested chat processing, keyset publication for E2EE, and signed receipts. |
| **Edge** | Metering front in front of the gateway: validates API keys / credits and forwards traffic. Under E2EE it should only see ciphertext for message content. |

Builders who want evidence for the model node specifically use the FOSS verify toolkit’s model check (operator provider key required for that one script). See [Verify Confidential AI](verify.md).

## Client contract

* Request body: OpenAI-compatible `/v1/chat/completions` with `"model": "gpt-oss-120b"`.
* Cost: **1 credit** per successful completion on the current testnet metering rules.
* E2EE: when using ACI v2, the model id is part of the associated data (AAD). Changing `MODEL` without matching the ciphertext binding will fail decryption / verification.

## What is not available (today)

* No multi-model picker in the chat UI — only `gpt-oss-120b` is published on this deployment.
* No guarantee of permanent model id stability across redeploys; if operators change the served model, docs and `MODEL` will need to match.

## Read next

* [Confidential AI overview](overview.md)
* [Chat UI](chat-ui.md)
* [Verify Confidential AI](verify.md)
