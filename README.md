# Basic CEX/DEX Comparator

A price gap between an exchange and a decentralised pool only matters at the size you can actually trade. Basic CEX/DEX Comparator is a colour terminal dashboard that streams live DNX trades from MEXC and Gate.io and compares them with Uniswap V3 quotes at several trade sizes, adding the gas cost of the swap. It helps a trader see in one screen which side is cheaper to buy or sell and whether a route survives its costs.

## Tech stack

| Layer | Technologies |
|---|---|
| Application | Python with asyncio, a Colorama terminal interface |
| Exchange data | MEXC and Gate.io WebSocket trade streams |
| On-chain quotes | Web3.py and Uniswap V3 pool quotes through an Ethereum node |
| Reference prices | ETH price from a Binance WebSocket, gas price from the node |
| Optional web view | A small Flask and HTML wrapper |

## Live exchange trades

The top of the screen follows the latest DNX/USDT trades from MEXC and Gate.io as they happen, so the current traded price on each exchange is always visible. An optional panel compares the two exchanges and shows the spread between them, which makes it easy to see when one venue is quoting the pair noticeably above the other. Trades scroll in with a compact time stamp, so the freshness of each price can be judged at a glance.

## Uniswap V3 quotes by size

For each configured trade size the dashboard asks the Uniswap V3 pool for a buy and a sell price, so the effect of price impact is visible as the size grows. Sizes can be set in DNX or in USD, and one key press cycles through four amount modes that combine both.

## Gas and best route

The dashboard shows the ETH price and the node gas price, and turns them into an estimated cost of the swap. A best-route panel highlights the direction with the largest gap after that cost, which separates a gap that looks good from one that can be traded.

## Display options

Command-line flags hide background logging, the quote lines, the best-route panel or the exchange comparison, and choose compact time stamps and the amount mode, so the same program serves a full analysis screen or a minimal ticker. A web wrapper with a simple HTML page can show the same comparison in a browser for users who prefer it to a terminal window.

## Scope and limits

The comparison covers the DNX pair on the supported exchanges and one Uniswap V3 pool. Some exchange streams can refuse connections from certain networks; the other exchange and the on-chain quotes keep working in that case.

---

Private code: [basic-cex-dex-comparator](https://github.com/logicencoder/basic-cex-dex-comparator)

See [REPOS.md](REPOS.md) for related repositories.

**[Logic Encoder](https://logicencoder.com)** · [GitHub](https://github.com/logicencoder) · [Contact](https://logicencoder.com/contact/)

<!-- TODO(screenshots, 2026-11-07): a terminal screenshot -->
