# Neptune L1 testnet wallet

**XNT Wallet** 0.3.9 (build `d80f3734`) is the wallet for **Neptune L1 testnet** (native **XNT**). It is a different app from the [Leviathan Chrome extension](chrome-extension.md), which is the programmable-layer wallet.

Testnet only. Assets have no real-world value. These builds are not store listings. Windows is not available yet.

All files, plus `SHA256SUMS`, are in the [XNT Wallet download folder](https://drive.google.com/drive/folders/1qf1fHQTYePueFCtFAUx9YU8Gv1Zorg18).

{% file src="https://drive.google.com/uc?export=download&id=1WGJtbZ2yMRb_xEjWxgw3SnL-8vIz80zD" %}
macOS Apple Silicon (M1 or newer) — XNT-Wallet-Leviathan-0.3.9-macos-arm64.dmg
{% endfile %}

{% file src="https://drive.google.com/uc?export=download&id=1elHCC6bphAa0VfCQSrRSFpb7OBxaxlbP" %}
Linux x86_64 (Ubuntu 22.04 or newer) — XNT-Wallet-Leviathan-0.3.9-linux-x86_64.AppImage
{% endfile %}

{% file src="https://drive.google.com/uc?export=download&id=16UJGJMvFBOleeUKhdeewxVQ0McwDVZw7" %}
Android arm64 (Android 7.0 or newer) — XNT-Wallet-Leviathan-0.3.9-android-arm64.apk
{% endfile %}

## Check the download

`SHA256SUMS` is in the same folder.

```bash
sha256sum -c SHA256SUMS
```

On macOS:

```bash
shasum -a 256 -c SHA256SUMS
```

| File | SHA-256 |
|------|---------|
| `XNT-Wallet-Leviathan-0.3.9-android-arm64.apk` | `4590e4fe302a7e636a4a423b2af9ba593e55706af94f81a7f4966470f0dc56fc` |
| `XNT-Wallet-Leviathan-0.3.9-macos-arm64.dmg` | `772d9add5f17f7b5d008bfb6b189bf41627111204ddab16fdaaaaf5c3fb9257b` |
| `XNT-Wallet-Leviathan-0.3.9-linux-x86_64.AppImage` | `1fed9b9adbe8f6be75c83b14dbe2420dd861c7409503e6d3e9703b2a02c7e5b2` |

## Install

**macOS.** Open the `.dmg` and drag XNT Wallet to Applications. The app is not signed. The first launch: right-click or Control-click **XNT Wallet**, choose **Open**, then **Open** again.

**Linux.**

```bash
chmod +x XNT-Wallet-Leviathan-0.3.9-linux-x86_64.AppImage
./XNT-Wallet-Leviathan-0.3.9-linux-x86_64.AppImage
```

**Android.** The APK is signed with a test key. Allow **Install unknown apps** for the browser or file manager, then open the `.apk`. This is not a Play Store build.

## Using it

Settings, then **Transactions**, controls max inputs per transaction and low-memory proving. Phones default to 3 inputs and low-memory proving on.

Bridge withdrawals from Leviathan back to XNT show in the balance and in History as **Bridge from Leviathan**. If you used an older build, open the **UTXO** tab and run **Force rescan from block 0** once so earlier withdrawals are found.

## Related

* [Leviathan Chrome extension](chrome-extension.md) for the programmable layer
* [Wallets overview](README.md)
