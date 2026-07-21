# TEE proving FAQ

Short answers to questions pioneers and builders ask once they start using delegated proving. For the full model, see [Attestation and trust](attestation.md). For commands, see [Set up delegated TEE proving](setup.md).

## Local proving vs delegated TEE proving

**When should I prove locally?**
When you are debugging client behavior, when the transaction is light enough that your machine finishes quickly, or when you do not want the prove payload to leave your environment at all.

**When should I use `--delegate-proving`?**
When you are on the `leviathan-client` path and wall-clock time or machine resources make local STARKs painful — especially multi-note consumption and repeated test loops. The client still builds and submits the transaction; only proof generation moves into the attested enclave.

**Does delegated proving replace the browser wallet?**
No. The [browser wallet](../getting-started/create-wallet.md) is still the simplest pioneer path for ordinary WXNT sends. TEE delegation is a CLI capability for builders who need remote attested proving.

**Does the chain treat TEE proofs differently from local proofs?**
No. The network verifies a STARK. It does not care whether your laptop or the enclave produced it, as long as the proof is valid.

## Keys, chat, and access

**What should I never paste into Discord, Telegram, or email?**
Your raw `tee_api_key`, wallet seeds, private keys, and exported `.mac` material that contains secrets. If the team asks for prover access material, send the **hash** of your API key, not the raw key.

**Why does the team only want the hash?**
So a leaked chat log does not hand someone a usable prover credential. You generate the secret locally; ops registers a one-way digest.

**I lost my raw API key. Do I need a new wallet?**
No. Generate a new key and hash, ask the team to attach the new hash and revoke the old one, then update `tee_api_key` in your config. Your testnet account ID can stay the same.

**Can someone prove as me if they only have the hash?**
They cannot use the hash as the client’s `tee_api_key`. Protect the raw key the same way you protect other long-lived secrets. If you suspect exposure, rotate immediately.

## Compose hashes and redeploys

**What is `tee_compose_hash`?**
The enclave measurement your client expects before it will pin TLS and prove. Think of it as a fingerprint of the live TEE composition, not as a password.

**How often does the hash change?**
Whenever ops redeploys or updates the Confidential VM in a way that changes the measured state (new image, certain restarts or resizes, new container identity paired with a new publish). There is no fixed calendar. On an active testnet it can be infrequent for days, then change when a prover image ships.

**What should I do when the team announces a new hash?**
Update `tee_compose_hash` (and URLs if they changed), save the config, and retry. You usually do not need to rebuild `leviathan-client`.

**My config used to work and now attestation fails. Is the cryptography broken?**
Usually not. The common case is a stale compose hash or container URL after a redeploy. Confirm against the latest team message before filing a protocol bug.

## Runtime behavior

**How long should a delegated prove take?**
Often tens of seconds for heavier `consume-notes` work; sometimes longer under load. Set `[remote_prover_timeout]` to at least **300 seconds** so the client does not give up while the enclave is still proving.

**I see “Fetching TEE attestation and pinning TLS cert…” — is that good?**
Yes. That is the client performing the confidence step. If prove succeeds without that line, you are probably not on the delegated TEE path you intended.

**What if the enclave is down?**
Delegated proves fail until it is back. Local proving (without `--delegate-proving`) may still work if your machine can handle the job. Testnet shared infrastructure will have maintenance windows.

**Does using the TEE mean the operator can spend my funds?**
No. The TEE path is not custody. Keys stay with you. The enclave receives a prove job and returns a proof; your client submits. Still follow normal key hygiene — attestation does not save a leaked seed.

## Trust and wording

**Is this trustless?**
No, and you should not market it that way. Operators still run Phala CVMs and publish hashes. Attestation lets your client verify it is talking to the published measurement over pinned TLS. That narrows trust; it does not delete operators.

**What does attestation actually guarantee?**
That the live enclave measurement matches what you configured (for the evidence path this stack uses), and that you can bind TLS to that attested identity before proving. It does not by itself audit the team’s release honesty, fix protocol bugs, or protect keys on your laptop.

**Where do I read the longer security explanation?**
[Attestation and trust](attestation.md).

## Getting unstuck

**Who do I ask for endpoints and access?**
Your Pioneer channel / Leviathan ops contact. Public docs intentionally do not hardcode ephemeral Phala container IDs.

**I followed the setup guide and still fail. What should I include in a report?**
Client version or git commit if known, whether attestation log line appeared, redacted config field names (not secrets), approximate timestamps, and the exact error text. Never attach raw API keys or seeds.

## Related pages

* [TEE proving overview](overview.md)
* [Attestation and trust](attestation.md)
* [Set up delegated TEE proving](setup.md)
* [STARK proofs](../technology/stark-proofs.md)
* [Glossary](../reference/glossary.md)
