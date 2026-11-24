# Evoxt Windows VPS: Which Plan Actually Runs Windows, Is $2.99 Enough, and How Do You Connect Over RDP? (Full Price, Bandwidth and Setup Guide)

The cheapest Evoxt plan that can run Windows is **VM-1 at $5.99/month**: 1 vCore, 2 GB RAM, 20 GB storage. The $2.99 VM-0.5 that Evoxt leads with on its homepage is cheaper, and it shows up in most "cheap Windows VPS" lists that mention the brand, but Evoxt's own dashboard documentation states that Windows is available only on VM-1 plans and above. If Windows is what you need, budget $5.99, not $2.99.

Below is the whole lineup with the prices on Evoxt's plan cards, why the 512 MB tier can't do the job even when a sales page implies it can, how your bandwidth allowance changes with the network class you pick, what a year actually costs, and the RDP steps including the one port detail most guides skip.

> **Quick pick: VM-1, $5.99/month.** 2 GB RAM, 20 GB storage, 1 TB transfer on the Standard network, weekly offsite backup included, and it's the first tier where Windows is an option. One MT4/MT5 bot, one scraping script, or one always-on desktop fits here. 👉 [Deploy VM-1 at the current price](https://bit.ly/EvoXt)

## The full Evoxt plan list and prices

Nine tiers appear on Evoxt's Windows RDP page, running from VM-0.5 to VM-8. All prices are USD per month, as printed on the plan cards.

| Plan | vCPU | RAM | Storage | Price (USD/mo) | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 | 512 MB | 5 GB | $2.99 | [Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 | 1 GB | 10 GB | $4.99 | [Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 | 2 GB | 20 GB | $5.99 | [Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 | 2 GB | 20 GB | $6.95 | [Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 | 4 GB | 30 GB | $11.99 | [Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 | 4 GB | 30 GB | $14.99 | [Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 | 8 GB | 60 GB | $23.99 | [Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 | 8 GB | 60 GB | $29.99 | [Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 | 16 GB | 80 GB | $47.99 | [Deploy VM-8](https://bit.ly/EvoXt) |
| VM-12* | 16 | 16 GB | 80 GB | $60.95 | [Deploy VM-12](https://bit.ly/EvoXt) |
| VM-16* | 16 | 32 GB | 100 GB | $95.99 | [Deploy VM-16](https://bit.ly/EvoXt) |

\*VM-12 and VM-16 are listed by independent plan trackers at these prices, but they don't appear on the Windows RDP page Evoxt publishes. If you need 16 cores, check that the tier exists in the console before you pay.

Two things about that table. The prices are monthly figures; longer prepaid terms are offered, but no annual price or annual discount is printed on the plan cards, so I won't quote one. And the RDP page's own benchmark comparison table carries a second, older set of prices for the same plans. The plan cards above are the ones the order flow uses.

## Can the $2.99 plan run Windows? What Evoxt's own documentation says

No, according to Evoxt's VM dashboard documentation, which puts it plainly: *"Windows OS is available only for VM 1 plans and above."* That single line moves the real entry price for an Evoxt Windows box from $2.99 to $5.99.

Documentation and sales pages drift, so check the OS dropdown in the order form before you pay. But even if the dropdown offered Windows on VM-0.5, 512 MB of RAM is not a Windows Server machine. Server Core idles in the high hundreds of megabytes; a full desktop session with a browser open needs well over a gigabyte before your application starts. You'd spend the first hour fighting the pagefile and the second hour fighting Windows Update.

You sometimes see the $2.99 tier described as "genuinely viable" for a stripped Server Core setup. Treat that as a project, not a purchase. If your goal is a Windows desktop you log into and use, the practical floor is VM-1's 2 GB.

## Pick a tier by what you're running

- **One MT4 or MT5 instance with an EA** → VM-1. Trading terminals are light on RAM and care about clock speed and latency to your broker, not core count. 2 GB leaves room for the terminal plus a browser.
- **Browser automation or scraping** → size by concurrency, not by cores. A Chrome instance runs 300–500 MB, so plan roughly 2 GB per parallel session: VM-4 ($23.99, 8 GB, 4 vCores) handles four to six at once, and its 4 TB Standard transfer covers most scraping volumes.
- **A shared desktop for 3–5 people** → VM-8 ($47.99, 16 GB, 8 vCores), plus RDS CALs from Microsoft. Windows Server includes two administrative RDP sessions by default; more simultaneous users need the Remote Desktop Services role and licences, which Evoxt doesn't sell.
- **A single always-on desktop** → VM-1 is the Windows floor. Step up to VM-2 ($11.99, 4 GB) only if you'll run Office plus a browser plus a background job at the same time.
- **Skip VM-1.5 unless you know why you want it.** It's $0.96 more than VM-1 for a second vCore and the same 2 GB of RAM. Windows desktop software is usually hungrier for memory than for cores, so that extra dollar buys less than the jump to VM-2.

## Same price, different bandwidth: Standard, Premium and Premium Plus

Evoxt sells the same VM in three network classes at the same monthly price, and the transfer allowance is what changes. This is the part that catches people out after they've picked a plan.

| Network class | Where | VM-1 transfer | VM-0.5 transfer |
| --- | --- | --- | --- |
| Standard | US, UK, Canada, Germany, Poland, Amsterdam, Tokyo, Malaysia, Australia (1 Gbps) | 1000 GB | 500 GB |
| Premium | Hong Kong, Osaka | 500 GB | 250 GB |
| Premium Plus | Malaysia, MyIX-peered | 300 GB | 150 GB |

Premium Plus is the only class where an entry tier costs more: VM-0.5 goes from $2.99 to $3.49. Everything above it matches Standard pricing.

Choose by where the other end of your connection sits, not where you sit. If your broker's servers are in London, a UK Standard VM beats a Hong Kong Premium VM with better ping to your laptop. If you're serving users in Hong Kong or Osaka, halving your bandwidth allowance for premium routing is usually the right trade. RDP itself is light on traffic; a desktop session idles in the tens of kilobytes per second, so the allowance matters when you're moving files or running a scraper, not when you're clicking around.

## What a year of Evoxt Windows actually costs

- VM-1: $5.99 × 12 = **$71.88**
- VM-2: $11.99 × 12 = **$143.88**
- VM-4: $23.99 × 12 = **$287.88**

Those are list prices with no discount applied. Plan trackers that re-read Evoxt's pages in late 2026 list the renewal rate as the same as the intro rate on every VPS tier, and a 7-day money-back window on the VPS plans (dedicated servers are excluded from refunds). The refund is what Evoxt actually received, so payment-gateway fees don't come back, and an abuse report on the service voids the guarantee entirely. Read those terms before you buy if there's any chance you'll want out.

Budget the twelve-month number, not the first invoice. $71.88 a year for a Windows box with 2 GB of RAM and a free weekly offsite backup is the actual comparison against whatever you're running now.

## Deploying and connecting over RDP

The flow is short. Average provisioning across six independent trials was 301 seconds, median 175, fastest 120, and Evoxt advertises about 2.5 minutes.

1. Create an account in the console. Name and email is the whole signup.
2. Pick a region from the list, using the network-class logic above.
3. Pick a plan. VM-1 or higher for Windows.
4. Pick Windows Server as the operating system.
5. Pay by card, PayPal, or crypto (Bitcoin, Litecoin, Ethereum, USDt on Tron). Crypto payments don't require KYC.
6. Wait for the welcome email with your IP, username and password.
7. Connect.

On Windows, press Win+R, type `mstsc.exe`, hit Enter. Paste the IP from the email into the Computer field, connect, accept the certificate warning on first connection, then log in. The username is usually `Administrator` and the password is in the same email. macOS users want Microsoft Remote Desktop from the App Store; on Linux, Remmina or `xfreerdp` both work.

Two settings worth changing on day one. Move RDP off port 3389 to something non-standard, which cuts most of the automated brute-force noise hitting every new Windows box within hours. Then enable Evoxt's panel firewall: it applies rules before traffic reaches the VM, and Evoxt's documentation notes it auto-allows TCP 3389 on Windows and TCP 22 on Linux so you don't lock yourself out while setting it up.

👉 [Start a Windows VM on the VM-1 tier](https://bit.ly/EvoXt)

## Performance numbers and what users report

Evoxt publishes GeekBench 5 multi-core scores on the same RDP page: VM-0.75 at 1073, VM-1 at 1098, VM-2 at 1940, VM-4 at 3306, VM-8 at 5265. The first two are effectively identical because both are single-core machines, which is another argument against paying $4.99 for VM-0.75 expecting more speed. You're buying RAM.

VPSBenchmarks, which has been testing Evoxt since 2022, scored VM-1 (February 2026) at 53 for performance but **80 price-weighted**, the best value score in the set. VM-4 came in at 60/69, VM-8 at 62/55, VM-2 at 34/57. Translation: the cheap single-core plan is where the price-to-performance case is strongest, and the bigger tiers are normal rather than exceptional.

Reviews are mixed in the usual budget-provider way. Trustpilot sits at 4 stars, and Evoxt quotes a customer of 1.5 years calling it "the best I could ask for." A Reddit thread in r/VPS titled "Evoxt, Worst VPS hosting service I've ever experienced" describes sustained connection failures and 100% packet loss on the IPv4 address. That's one user's experience, not an aggregate, and other Reddit threads recommend the brand specifically for high single-core clock speeds under €10. The free weekly offsite backup and sub-five-minute rebuilds are the practical hedge either way.

On DDoS protection the sources disagree: Evoxt's older product page says every server ships with it, while a 2026 third-party guide lists it as a paid extra. Ask in the panel or check the order form if that's a deciding factor for you.

## Discounts: where the promo field is

Evoxt runs rotating promotions, and the order form has a promo code field before checkout. Coupon aggregators list several codes, including first-month and recurring-discount offers, but none of them are confirmed on Evoxt's own pages and the codes rotate, so I'm not printing any here. Enter whatever you've found in that field and watch the invoice total change; if it doesn't change, the code is dead. 👉 [See what the order form quotes you today](https://bit.ly/EvoXt)

## FAQ

**Can I install Windows on the $2.99 plan?**
Per Evoxt's dashboard documentation, Windows starts at VM-1. The 512 MB of RAM on VM-0.5 wouldn't run a usable Windows desktop regardless.

**Is the Windows licence billed separately?**
Third-party guides say licensing is bundled and there's no separate line item. Evoxt's plan cards don't itemise a licence fee. Confirm on your invoice.

**How many people can log in over RDP at once?**
Two administrative sessions by default. More concurrent users require the RDS role plus CALs purchased from Microsoft.

**Do backups cost anything?**
Evoxt includes automatic weekly offsite backup on every plan at zero cost, including VM-0.5. Paid options exist if you want daily backups or longer retention.

**Which payment methods work?**
Credit and debit cards, PayPal, Bitcoin, Litecoin, Ethereum, and USDt on Tron.

## Before you order

Match the tier to the job: one bot or one desktop → **VM-1 at $5.99**. Four to six parallel browser sessions → **VM-4 at $23.99**. Three to five people sharing a desktop → **VM-8 at $47.99** plus RDS CALs from Microsoft. Anything below VM-1 is a Linux box, whatever the homepage banner suggests.

Then confirm two things at checkout: that Windows appears in the OS dropdown for the tier you picked, and which network class you selected, because that's what sets your transfer allowance rather than your price. 👉 [Open the Evoxt console and check both before paying](https://bit.ly/EvoXt)
