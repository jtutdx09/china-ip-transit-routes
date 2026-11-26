# China Optimized IP Transit: What the Three Premium Routes Really Are, What 10G Actually Costs, and How to Check a Provider's Claim Before You Sign (Plus the Small-Port Option Most Buyers Should Start With)

China optimized IP transit means one of three specific carrier products: China Telecom's CTGNet (AS23764 and AS4809), China Unicom's CUP (AS9929 and AS10099), or China Mobile's CMIN2 (AS58807). A provider selling "China optimized" transit without naming which of those three it hands you off to is selling a standard route with a better label. Published list prices from a US transit reseller put the three tiers roughly 1 : 5 : 85 apart at 10G: $700/month for standard international, $3,500/month for "China Optimized", $60,000/month for premium CN2. The middle tier usually runs on the standard backbone AS numbers, not the premium ones.

Below: the AS-number map with the naming traps, the price ladder converted to dollars per megabit, the utilization question that separates real capacity from a label, the four checks to run before signing, and the smaller option worth considering if you need 100 Mbps to 1 Gbps rather than a full 10G port.

> **Quick pick.** If you need China-optimized routing out of Los Angeles at port sizes below 1G, SixtyNet's China Unicom Premium offering is the cheaper entry: **$2,500.00 USD/year** (listed at $3,000.00, 17% off) for a 100M base port on AS9929 with 3× burst, 95th-percentile billing and free BGP session setup. Their LAX VPS plans on the same network start at **$200.00 USD/year**. 👉 [See SixtyNet's current AS9929 plans and pricing](https://sixtynet.net/aff.php?aff=39)

## SixtyNet's full plan list

SixtyNet does not publish 10G or 100G transit ports. What it sells from Los Angeles is a small AS9929 BGP port plus VPS capacity on the same China Unicom Premium network, billed annually.

| Plan | Specs | Network | Price (annual) | Order |
| --- | --- | --- | --- | --- |
| Los Angeles China Unicom-Premium | 100M base port, 3× burst, 95th-percentile billing | China Unicom Premium AS9929, free BGP session setup, limited BGP support | $2,500.00 USD (list $3,000.00) | [Order the AS9929 BGP port](https://sixtynet.net/aff.php?aff=39) |
| LAX-STARTER | 2 core, 2 GB RAM, 40 GB NVMe, 12,500 IOPS, 5 TB traffic | Premium network (2G) | $200.00 USD (list $240.00) | [Order LAX-STARTER](https://sixtynet.net/aff.php?aff=39) |
| LAX-MICRO | 4 core, 4 GB RAM, 80 GB NVMe, 12,500 IOPS, 10 TB traffic | Premium network (4G) | $400.00 USD (list $480.00) | [Order LAX-MICRO](https://sixtynet.net/aff.php?aff=39) |
| LAX-MEDIUM | 8 core, 8 GB RAM, 160 GB NVMe, 25,000 IOPS, 20 TB traffic | Premium network (10G) | $800.00 USD (list $960.00) | [Order LAX-MEDIUM](https://sixtynet.net/aff.php?aff=39) |
| LAX-LARGE | 8 core, 16 GB RAM, 320 GB NVMe, 25,000 IOPS, 40 TB traffic | Premium network (10G) | $1,600.00 USD (list $1,920.00) | [Order LAX-LARGE](https://sixtynet.net/aff.php?aff=39) |

Every LAX VPS tier carries DDoS protection. The listed "save 17%" is the gap between the struck-through price and the annual price, so the discount is baked into annual billing rather than a code you enter at checkout.

| Contract detail | What SixtyNet states |
| --- | --- |
| Billing | Annual prices above; the AS9929 port also offers a quarterly payment discount |
| Refunds | 3-day money-back guarantee, subject to their refund policy |
| Location | Los Angeles, Coresite LA2, Any2 peering |
| DDoS | Mitigation advertised at over 1000 Gbps on the network, DDoS protection included on LAX VPS plans |
| Support | 24/7 ticket support, with the caveat that investigation tickets may exceed the stated response window |
| Residential-IP variants | Same LA configurations up to 16 core / 16 GB / 320 GB with 40 TB traffic, but ports 80 and 443 are closed for IP risk-control reasons, and refunds on those products go to account balance only |

The residential-IP variants matter if you were planning to host a public website on them. You cannot. They are for outbound work, scraping, or anything that does not need inbound HTTP on standard ports.

## The three premium routes and the AS numbers to ask for

The single most useful question in this market is "which AS numbers am I transiting through", because the marketing names have drifted and providers mix them freely.

| Carrier | Product name | AS numbers | What it is |
| --- | --- | --- | --- |
| China Telecom | CTGNet, long marketed as CN2 GIA | AS23764 and AS4809 | Premium tier built on top of the CN2 backbone; designed to stay on China Telecom's own network longer instead of exiting through the same congested peering points standard traffic uses |
| China Unicom | CUP, also sold as CUII or CUG | AS9929 and AS10099 | Unicom's equivalent, with the same goal of fewer hops and less peak-hour congestion, applied to traffic bound for Unicom's network |
| China Mobile | CMIN2 | AS58807 | The newest of the three to appear widely in commercial hosting products; relevant if a meaningful share of your users are on China Mobile, mobile or fixed |

Two naming traps worth knowing. CTGNet is the name China Telecom currently uses for the product it spent years selling as CN2 GIA, and both terms remain in circulation, sometimes on the same provider's site in different places. On the Unicom side, CUII, CUP and CUG all refer to the same premium family, with AS9929 and AS10099 appearing in different combinations. If a sales rep cannot tell you which AS numbers your traffic will actually traverse, the label is decoration.

The harder constraint: the three carriers run separate networks with separate international gateways. A route tuned for China Telecom delivers nothing extra to a China Unicom user, and vice versa. If your audience skews toward one carrier, a route optimized for that carrier generally beats a route optimized for a different one, regardless of which is nominally "better".

## Why a cheap "China Optimized" port often never touches the premium layer

Look at how a real price sheet is structured. On CnServer's public IP transit page, three tiers coexist:

| Tier | 10G list price | Per Mbps | 100G list price | Per Mbps |
| --- | --- | --- | --- | --- |
| Standard international | $700/mo | $0.07 | $4,000/mo + $1,500 setup | $0.04 |
| China Optimized | $3,500/mo | $0.35 | $35,000/mo + $1,500 setup | $0.35 |
| China Premium (CN2 GIA, AS10099, CMIN2) | $60,000/mo | $6.00 | $600,000/mo + $1,500 setup | $6.00 |

The per-megabit figures are arithmetic on those list prices, not quoted rates. What matters is what the tiers contain. The standard tier lists Hurricane Electric, Cogent, GTT, Lumen and Arelion. The China Optimized tier lists China Telecom AS4134, China Unicom AS4837 and China Mobile AS58453, which are the standard backbones (163, 4837 and CMI), not the premium routes. Only the $60,000 tier names CN2 GIA, AS10099 and CMIN2.

That is where the 85× gap comes from, and it is the easiest place to overpay. If a provider quotes you something in the low thousands per 10G and calls it China optimized, the AS list will usually show 4134, 4837 and 58453. You are buying better-peered standard transit, not premium capacity. That can be entirely adequate. It is not the same product.

Also note that the 10G and 100G China Optimized tiers work out to the same $0.35/Mbps, so the small port carries no volume penalty at list. A Hong Kong provider separately advertises US access from $0.33/Mbps, though without stating the port size or term, which lands in the same range and cross-checks the magnitude rather than the exact number.

One more thing to read carefully: the standard disclaimer on these pages says China routing performance may vary by destination carrier, region, upstream policy, congestion and service location, and that fixed latency or a fixed AS path is not guaranteed unless separately agreed in writing. Assume the same default applies everywhere. If latency is contractual, put it in the contract.

If your requirement is a few hundred megabits rather than ten gigabits, the premium-tier economics stop making sense and a smaller AS9929 port does the same job for a fraction of the spend. 👉 [Check SixtyNet's AS9929 port pricing and terms](https://sixtynet.net/aff.php?aff=39)

## The question that beats "is it CN2?"

Ask what utilization ceiling the provider keeps on the premium path, and ask it in writing. A premium route that is oversold behaves like a standard route at 21:00 Beijing time.

One Hong Kong provider states plainly that its CN2 GIA path is held at no more than 50% network bandwidth utilization, and sells that as the product. That number is more informative than any mention of CN2 in a feature list, because it describes the operating discipline rather than the name of the carrier product. Vendors in this space routinely advertise 30–50 ms averages and sub-0.1% packet loss, but almost none publish the test points, the measurement hours, or commit those figures contractually. Treat latency claims without a methodology as advertising.

Practical version of the question: what is the utilization cap on my committed bandwidth, what does the 95th percentile look like on your China paths during 20:00–23:00 CST, and will you put a latency or loss threshold in the agreement with a credit mechanism if it is missed.

## Four checks before you sign

1. **Get the AS numbers per destination carrier.** Ask separately for China Telecom, China Unicom and China Mobile. A single generic "China optimized" answer means one path, not three.
2. **Run a traceroute from and to a China IP.** What you want to see is your traffic staying on the relevant carrier's own backbone for a meaningful stretch, rather than hopping onto another network early. If most of the path is on a third-party transit provider, you bought the standard tier.
3. **Test repeatedly, at different hours.** A single afternoon test tells you almost nothing. Some providers oversubscribe their optimized capacity and the evening peak is where it shows. Sample several days across peak and off-peak.
4. **Ask for a test IP, a trial, or a looking glass.** A provider with genuine premium capacity usually has nothing to hide here. If there is no way to test before paying, price that risk in.

## Where SixtyNet fits, and what it does not sell

SixtyNet is a small Los Angeles operator, and its AS9929 port is the closest thing in its catalogue to China-optimized transit. At $2,500/year for a 100M base port with 3× burst on 95th-percentile billing, the effective cost is far below anything on the premium 10G ladder, and 95th-percentile metering means short spikes do not count against you. It suits game servers, a cross-border SaaS backend, small hosting operations, or a secondary China path next to a primary carrier.

Limits you should know before ordering. There are no 10G or 100G transit products published, so this is not a wholesale option. BGP technical support is described as limited, with free session setup. Third-party BGP records for SixtyNet's AS60699 show two upstreams and no announced IPv6 prefixes, with the registry record last updated in early 2025. If IPv6 reachability into China is on your requirements list, ask about it directly rather than assuming. And confirm the physical handoff and port type with sales before you pay, since the AS9929 product is listed on the VPS page rather than a dedicated transit page.

## Who should not buy this

- **China-facing traffic is a small slice of your total.** If it is a few percent, a well-located server elsewhere in Asia usually gets you most of the benefit for none of the premium.
- **Your users concentrate on one carrier and you are buying another carrier's optimization.** A CTGNet route will not rescue an audience that lives on China Unicom.
- **You need guaranteed latency but will not negotiate it into the contract.** The default terms on every price sheet in this market disclaim fixed latency and fixed AS paths.
- **You need one server, not a network.** A China-optimized VPS handles that. A transit port is infrastructure you resell or route behind.

## FAQ

**Does China optimized transit guarantee good performance everywhere in China?** No. Routing quality varies by destination city and network, not just by carrier. Two users on the same carrier in different provinces can see different results.

**Is it much more expensive than standard transit?** At 10G list prices, roughly 5× for the China Optimized tier and about 85× for premium CN2. Actual pricing moves with committed bandwidth and contract length, so those multiples are a starting point, not a quote.

**Do the three carriers' optimizations stack?** No. Each premium product only helps traffic destined for that carrier's own network. Serving all three well means three separate paths or a provider that buys all three.

**Can I test before committing?** You should insist on it. Ask for a test IP, a short trial, or a public looking glass, and test during Chinese evening peak rather than at 10:00 UTC.

**What does "lightly loaded" mean in practice?** A premium carrier network deliberately kept at low utilization, as opposed to a standard backbone carrying heavy evening traffic. It shows up as steadier latency and less jitter, not necessarily a lower average number.

## Picking a path

Match the product to the port size, not to the label. Under about 1 Gbps of China-bound traffic, a China-optimized VPS or a small AS9929 BGP port is the rational buy, and paying premium 10G rates for that volume is waste. Between 1G and 10G with latency-sensitive traffic across all three carriers, you are in China Optimized or premium territory and should be comparing AS lists line by line. Above 10G, you are negotiating, and the list prices in this article are only there to tell you when someone is quoting you a standard route at a premium price.

Before you pay anyone, confirm three things: the specific AS numbers per destination carrier, the utilization ceiling on your committed bandwidth, and whether latency or loss commitments are written into the agreement with a remedy attached. Everything else is sales copy.

👉 [Start with SixtyNet's AS9929 port or LAX plans](https://sixtynet.net/aff.php?aff=39)
