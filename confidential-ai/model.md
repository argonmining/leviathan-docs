# Models

Private AI serves a **live catalog** of open-weight models inside attested TEEs. The hosted [chat UI](https://ai-tee-leviathan.up.railway.app/) defaults to:

```text
qwen3.8-27b
```

The toolbar **Model** picker lists whatever the Edge catalog returns. As of the public testnet docs, that set includes `deepseek-v4-flash`, `glm-5.1`, `glm-5.2`, `qwen3.6-35b-a3b`, and `qwen3.8-27b`.

`gpt-oss-120b` was removed from the upstream catalog. Do not send that id.

The model id is what clients put in OpenAI-compatible `model` fields, and what E2EE associated data binds to for each exchange.

## How Leviathan runs inference

| Layer | Role |
|-------|------|
| **Model node** | Serves the selected open-weight model inside an **NVIDIA GPU-TEE**. |
| **Gateway TEE** | Intel **TDX** enclave for attested chat processing, the E2EE keyset, and signed receipts. |
| **Edge** | Metering front: checks credits and forwards traffic. Under E2EE it should only see ciphertext for message content. |

## Client contract

* Request body: OpenAI-compatible `/v1/chat/completions` with a catalog `model` id.
* Cost: **1 credit** per successful completion.
* E2EE: the model id is part of the associated data. The ciphertext must be sealed for the same id you send.

## Read next

* [Confidential AI overview](overview.md)
* [Chat UI](chat-ui.md)
* [Credits](credits.md)
* [Verify Confidential AI](verify.md)
