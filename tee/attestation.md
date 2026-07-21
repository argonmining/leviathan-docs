# Attestation and trust

If you are going to send prove jobs off your machine, you should know exactly what “attested” means here, what the client checks, and what remains outside the enclave’s guarantees. This page is the confidence document for the TEE path. It is written for builders and careful readers, not for slogans.

## What a TEE is doing in this stack

A Trusted Execution Environment is a hardware-isolated place to run code. Leviathan’s current testnet prover uses Intel TDX on Phala Cloud: a Confidential VM whose memory and execution are isolated from the ordinary host OS and from other tenants in ways the TDX model is designed to enforce.

Inside that VM, Leviathan runs:

1. **`leviathan-remote-prover`** — the STARK prover listening on an internal port (`50051`). It is not exposed directly to the internet.
2. **Attestation proxy** — terminates TLS for clients, exposes `/tls-attestation`, rate-limits attestation calls, and forwards prove requests to the local prover.

Your laptop is still authoritative for keys and for the decision to submit a transaction. Phala still routes packets. The enclave is where *proof generation* happens after your client is satisfied with the attestation.

## What “attestation” means here

Attestation is evidence, signed through the hardware and platform stack, that a particular software composition is running in a genuine TEE. In Leviathan’s client flow, that evidence is fetched from the enclave’s HTTPS `/tls-attestation` endpoint before proving.

The client then does two important things:

1. **Checks the compose hash** — a measurement associated with the enclave’s runtime state (including RTMR3 in this Phala/dstack setup). Your config must match the hash the team published for the live deployment.
2. **Pins the TLS certificate** presented in that attestation path — so subsequent prove traffic is bound to the identity you just verified, not to whatever certificate a middlebox might invent later.

When things are working you will see a log line like:

```text
Fetching TEE attestation and pinning TLS cert...
```

Treat that as a security step. If it fails, stop and fix configuration. Do not look for a way to skip the check.

## Why the Phala `s` URL suffix matters

Phala publishes service URLs that encode the container and port. For this stack:

| Port | Purpose | Config key |
|------|---------|------------|
| `50052` | gRPC over HTTPS for proving | `remote_prover_endpoint` |
| `50053` | HTTPS REST for attestation | `tee_attestation_url` |

The `s` in URLs such as `…-50052s.dstack-…` requests **TLS passthrough** to the CVM. The TLS handshake is between your client and software inside the enclave. That is different from a gateway that terminates TLS and forwards plaintext into a container.

Combined with certificate pinning after attestation, this is the main network-level defense against a simple on-path attacker impersonating the prover.

## What you put in client config

A typical TEE block in `~/.leviathan/leviathan-client.toml` looks like this (values come from the team):

```toml
remote_prover_endpoint = "https://<CONTAINER_ID>-50052s.dstack-pha-prod9.phala.network"
tee_attestation_url = "https://<CONTAINER_ID>-50053s.dstack-pha-prod9.phala.network/tls-attestation"
tee_compose_hash = "<published hex measurement>"
tee_api_key = "<your locally generated raw key>"
```

| Field | Role |
|-------|------|
| `remote_prover_endpoint` | Where delegated prove RPCs are sent |
| `tee_attestation_url` | Where attestation evidence is fetched |
| `tee_compose_hash` | Expected enclave measurement; must track redeploys |
| `tee_api_key` | Access credential for the shared testnet prover (raw secret stays on your machine) |

Think of `tee_compose_hash` as a firmware fingerprint for the live prover image and composition. When ops rebuilds the image, restarts the CVM in ways that change measurements, or moves to a new container ID, the published hash (and sometimes the URLs) change. Update your config from the team’s notice. Stale hashes fail closed; that is the correct behavior.

## What leaves your machine during delegated proving

Be precise about data flow:

* **Stays local:** seed material, long-term keys, your decision to submit, and your copy of chain state after sync.
* **Sent to the enclave:** the prove request payload required to generate the STARK for that transaction (the remote prover API), authenticated under your provisioned access credential.
* **Returned to you:** the proof (and related prove response data) so the client can submit to the network.
* **Sent to the network by you:** the proven transaction, same as after a local prove.

The TEE path is not a custodial wallet. It is a remote proving service with attestation. If a transaction should never leave a particular environment even as a prove job, do not delegate that job.

## How the prover image is built (and why that matters)

The enclave runs a container image built from the Leviathan multi-repo tree (`node` plus sibling `protocol`, `crypto`, and `miden-vm` checkouts). The Dockerfile in `node/phala-TEE` is written for a careful release build: base images pinned by digest, Rust builds with `--locked`, and `SOURCE_DATE_EPOCH` support for more reproducible timestamps. The runtime image drops privileges to a non-root user and starts both the prover and the attestation proxy so that if either process dies, the container exits and can be restarted cleanly.

You do not need to rebuild the image to use the service. Confidence for most pioneers comes from:

1. Using the **compose hash** the team published for the live CVM
2. Letting the client **reject mismatches**
3. Knowing that a redeploy is announced as a **new hash**, not a silent swap

Engineers who want to inspect the implementation should read the `phala-TEE` directory in the `node` repository: attestation proxy, Dockerfile, Phala compose file, and entrypoint script.

## Trust boundaries

### Strengthened by this design

* Prove work runs in a TDX-isolated VM rather than an ordinary shared process you cannot measure.
* Clients can bind to a specific published measurement before proving.
* TLS can be pinned to the attested enclave identity after that check.
* Operational changes to the enclave are visible as hash and URL updates.

### Not removed by this design

* Protocol bugs, client bugs, and user key compromise are still in scope.
* Attestation checks that the live measurement matches what you configured. It does not, by itself, prove that the humans who published the hash chose a benign image. You are trusting the Leviathan team’s release process and communications for “this hash is the intended prover.”
* Phala and network availability still matter. An attested enclave that is down cannot prove for you.
* Access to the shared testnet prover is gated. That is operational control of a scarce resource, not a claim about on-chain economics.

A careful sentence for external writing:

> Delegated proving runs in an attested Intel TDX enclave. The client verifies the enclave measurement and pins TLS before the prove job runs.

Avoid calling the system “trustless cloud proving.” Operators still exist. The point of attestation is to narrow what you must believe about them, not to pretend they vanished.

## Practical self-checks

Before you rely on a session:

1. Confirm your three endpoint fields match the latest team message (container ID and compose hash drift together more often than people expect).
2. Confirm `[remote_prover_timeout]` is high enough (300 seconds is the documented floor for heavy `consume-notes` work).
3. On first prove, watch for the attestation log line. If it never appears, you are not on the TEE path you think you are.
4. After any announced redeploy, update `tee_compose_hash` before filing a bug.

## Related reading

* [Set up delegated TEE proving](setup.md)
* [TEE proving overview](overview.md)
* [TEE proving FAQ](faq.md)
* [STARK proofs](../technology/stark-proofs.md)
* [Glossary](../reference/glossary.md)
