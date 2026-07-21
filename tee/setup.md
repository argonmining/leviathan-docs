# Set up delegated TEE proving

This guide takes you from a clean machine to a successful Leviathan testnet transaction proven inside the team-hosted TEE. You will build `leviathan-client`, create a wallet, configure attestation endpoints, and run `consume-notes` / `send` with `--delegate-proving`.

It assumes you can use a terminal. It does not cover the browser wallet (see [Create a wallet](../getting-started/create-wallet.md)) or bridge UI.

Before you start, ask the team (Pioneer channel / ops) for the live prover values:

* `remote_prover_endpoint`
* `tee_attestation_url`
* `tee_compose_hash`

You will also complete a short access step so the shared enclave is not an open relay ([Step 4](#step-4--get-access-to-the-shared-prover)).

If you want the security model first, read [Attestation and trust](attestation.md), then come back here.

---

## What you will have at the end

* A release build of `leviathan-client` on your `PATH`
* A testnet wallet under `~/.leviathan/`
* Client config that attests the live Phala enclave before proving
* At least one successful delegated prove (consume or send)

Expected wall time: most of an afternoon the first time, mostly waiting on the Rust compile and on ops replies. Later runs are much faster.

---

## Prerequisites

* Linux or macOS. Ubuntu 22.04 / 24.04 is a known-good baseline.
* Disk space for a large Rust workspace (plan for several GB during compile).
* Rust **1.93 or newer** from [rustup](https://rustup.rs/). Distro packages are often far too old; do not use `apt install cargo` as your toolchain.
* Git, OpenSSL (or LibreSSL), `curl`, and `jq`.

### Ubuntu packages

```bash
sudo apt update
sudo apt install -y \
  build-essential \
  pkg-config \
  libssl-dev \
  libclang-dev \
  cmake \
  protobuf-compiler \
  curl \
  jq \
  git \
  openssl \
  ca-certificates
```

### Rust via rustup

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source "$HOME/.cargo/env"
rustc --version
cargo --version
```

You want `rustc` reporting 1.93.x or newer.

### macOS notes

Install a recent Xcode command-line tools stack and use rustup the same way. For hashing in Step 4, macOS often has `shasum` rather than `sha256sum`:

```bash
HASH=$(printf '%s' "$RAW_KEY" | shasum -a 256 | awk '{print $1}')
```

---

## Step 1 — Clone the multi-repo workspace

Leviathan crates depend on sibling repositories by relative path. Clone them next to each other under one parent directory.

```bash
mkdir -p ~/workspace/leviathan
cd ~/workspace/leviathan

git clone -b tee-port https://git.softly.com/leviathan/leviathan-client.git
git clone -b feat/TEE-offchain-payment-v0.15 https://git.softly.com/leviathan/node.git
git clone -b next https://git.softly.com/leviathan/protocol.git
git clone -b next https://git.softly.com/leviathan/miden-vm.git
git clone -b v0.23.0 https://git.softly.com/leviathan/crypto.git
```

You should see:

```text
~/workspace/leviathan/
  ├── leviathan-client/
  ├── node/
  ├── protocol/
  ├── crypto/
  └── miden-vm/
```

Branch names move as the TEE work lands. If a clone fails or the team posts newer refs, use what they publish for the TEE-enabled client. The branch name on `node` may still mention older feature work; that is a git label, not an invitation to configure payments in this guide.

---

## Step 2 — Build and install the client

```bash
cd ~/workspace/leviathan/leviathan-client
cargo build --release --bin leviathan-client
```

The first build compiles a large dependency graph. Ten to fifteen minutes on a typical laptop is normal; slower machines can take longer.

Put the binary on your `PATH` (symlink example):

```bash
sudo ln -sf "$(pwd)/target/release/leviathan-client" /usr/local/bin/leviathan-client
leviathan-client info
```

If `info` runs, the binary is wired correctly. Network fields may look empty until after `init`.

---

## Step 3 — Initialize and create a wallet

Point the client at Leviathan testnet and create a public wallet account:

```bash
leviathan-client init --network "http://testnetnative.neptune.io:57291"
leviathan-client new-wallet -s public
```

Copy the **30-character hex account ID** from the success message. You will pass it to `--account` and `--target` later.

If you need assets, ask the team for a testnet mint or funding path. The CLI pioneer flow does not assume a public faucet page. After a mint lands, always `sync` before consuming.

---

## Step 4 — Get access to the shared prover

The enclave is shared infrastructure. Access is provisioned per pioneer so the prover is not a free-for-all endpoint on the open internet.

Generate a 256-bit key on your own machine:

```bash
RAW_KEY=$(openssl rand -hex 32)

# Linux:
HASH=$(printf '%s' "$RAW_KEY" | sha256sum | cut -d' ' -f1)

# macOS (if sha256sum is missing):
# HASH=$(printf '%s' "$RAW_KEY" | shasum -a 256 | awk '{print $1}')

echo "RAW_KEY (keep private): $RAW_KEY"
echo "HASH (send to the team): $HASH"
```

Store `RAW_KEY` in a password manager. Send **only** `HASH` through your pioneer channel. The team registers the hash and returns (or confirms) the live endpoint trio and that your credential is active.

Why hash-only registration: if chat history leaks, an attacker gets a one-way digest, not a usable API secret. The client keeps the raw key locally and derives what the service expects.

### If you lose the raw key

Generate a new `RAW_KEY` / `HASH` pair the same way. Ask the team to attach the new hash to your existing access and revoke the old hash. You should not need a new wallet for that rotation.

---

## Step 5 — Configure TEE settings

Edit `~/.leviathan/leviathan-client.toml` and set the values the team gave you:

```toml
remote_prover_endpoint = "https://<CONTAINER_ID>-50052s.dstack-pha-prod9.phala.network"
tee_attestation_url = "https://<CONTAINER_ID>-50053s.dstack-pha-prod9.phala.network/tls-attestation"
tee_compose_hash = "<compose_hash_from_team>"
tee_api_key = "<RAW_KEY from Step 4>"
```

Also raise the remote prover timeout. Complex `consume-notes` proofs regularly need tens of seconds inside the enclave; a twenty-second client timeout will abort while the prover is still working:

```toml
[remote_prover_timeout]
secs = 300
nanos = 0
```

Details on what these fields mean: [Attestation and trust](attestation.md).

---

## Step 6 — Consume a note with delegated proving

Once your account has a claimable note (mint or incoming transfer) and you have synced:

```bash
leviathan-client sync

leviathan-client consume-notes \
  --account <YOUR_WALLET_ID> \
  --delegate-proving \
  --force
```

A healthy run looks roughly like this:

```text
Nonce incremented by: 1.
Proving transaction...
Fetching TEE attestation and pinning TLS cert...
...
Successfully created transaction.
Transaction ID: 0x...
```

If attestation succeeds and the transaction ID prints, you are on the TEE path end to end.

---

## Step 7 — Optional: send with delegated proving

Create a second wallet, inspect assets on wallet A, then send to wallet B. Replace the asset string with an amount and faucet or token ID from `account -s` on your synced wallet.

```bash
leviathan-client new-wallet -s public
# copy wallet B id from the output

leviathan-client account -s <wallet_A_ID>

leviathan-client send \
  --target <wallet_B_ID> \
  --asset '<amount>::<FAUCET_OR_TOKEN_ID>' \
  --note-type public \
  --delegate-proving \
  --force
```

On wallet B:

```bash
leviathan-client sync
leviathan-client consume-notes \
  --account <wallet_B_ID> \
  --delegate-proving \
  --force
```

---

## Troubleshooting

| What you see | Likely cause | Fix |
|--------------|--------------|-----|
| Prove hangs then times out | Client timeout too low | Set `[remote_prover_timeout] secs = 300` |
| Compose hash / attestation failure | Enclave redeployed or typo in hash | Ask for the current `tee_compose_hash` (and URLs); update config |
| Unauthorized / auth errors | Hash not registered or wrong `tee_api_key` | Confirm provisioning; paste the raw key, not the hash, into `tee_api_key` |
| `leviathan-client: command not found` | Binary not on `PATH` | Redo the symlink in Step 2 |
| Compile errors about the Rust edition or language version | Toolchain older than 1.93 | Reinstall with rustup; verify `rustc --version` |
| Nothing to consume | Wallet empty or not synced | Request a mint, wait for inclusion, run `sync` |
| Build cannot find sibling crates | Repos not side by side | Recheck the directory layout in Step 1 |

If attestation fails, fix the published values. Do not disable checks to “just get a proof.”

### After an enclave redeploy

Ops will publish a new compose hash and sometimes new container URLs. Update `leviathan-client.toml`, save, and retry. You do not need to rebuild the client for a hash rotation.

---

## Sanity checklist

Use this before you declare the setup broken:

1. `rustc --version` is ≥ 1.93
2. `leviathan-client info` runs
3. `init` used `http://testnetnative.neptune.io:57291`
4. `tee_api_key` is the **raw** key; the team only ever received the **hash**
5. Endpoint hostnames use the `s` suffix ports (`50052s` / `50053s`) as provided
6. Timeout is 300 seconds
7. You ran `sync` after any mint

---

## What success means

You have shown that your client can:

* Verify the live enclave measurement
* Pin TLS to that enclave
* Obtain a STARK from inside TDX
* Submit a transaction the testnet accepts

That is the intended pioneer outcome for this path. For the surrounding architecture, see [TEE proving overview](overview.md) and [Attestation and trust](attestation.md). For common questions (local vs delegated, chat hygiene, hash rotation), see the [TEE proving FAQ](faq.md). For why proofs exist at all, see [STARK proofs](../technology/stark-proofs.md).
