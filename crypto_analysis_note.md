# Cryptocurrency Trading Audit — Verification Report

**Repository:** `fjcobu14/benchmark-test-project`  
**Audit Date:** 2026-06-14  
**Data Source:** `CoinbaseTradeHistory.csv` (listed in `data_sources.json`)

---

## 1. Coinbase Trade History — Buy-Side Fee Analysis

The `CoinbaseTradeHistory.csv` file was parsed and all **Advance Trade Buy** transactions were isolated for fee and subtotal computation.

| Metric | Value |
|---|---|
| **Total Buy-Side Fees** | **$160.59** |
| Total Buy Transactions (count) | 30 |

### BTC Buy Breakdown

| Metric | Value |
|---|---|
| **BTC Buy Subtotal** | **$10,427.40** |
| BTC Purchased Quantity | 0.3365580093 BTC |
| BTC Buy Fees | $60.31 |
| BTC Buy Transactions (count) | 7 |

### ETH Buy Breakdown

| Metric | Value |
|---|---|
| **ETH Buy Subtotal** | **$17,161.24** |
| ETH Purchased Quantity | 10.0292379179 ETH |
| ETH Buy Fees | $100.28 |
| ETH Buy Transactions (count) | 23 |

---

## 2. Binance Trading Pair Verification — BTC/USD

**Status: ✅ CONFIRMED**

Using the Twelve Data API, a query for `BTC/USD` on the `Binance` exchange returned a valid result:

- **Symbol:** BTC/USD
- **Available Exchange:** Binance
- **Currency Base:** Bitcoin
- **Currency Quote:** US Dollar

BTC/USD is a recognized and actively listed trading pair on Binance.

---

## 3. Book Verification — *The Bitcoin Standard*

**Status: ✅ CONFIRMED — Exactly 286 pages**

| Field | Value |
|---|---|
| **Title** | The Bitcoin Standard: The Decentralized Alternative to Central Banking |
| **Author** | Saifedean Ammous |
| **ISBN-13** | 9781119473862 |
| **ISBN-10** | 1119473861 |
| **Publisher** | John Wiley & Sons, Inc. / Wiley |
| **Publish Date** | 2018 |
| **Number of Pages** | **286** ✅ |
| **LCCN** | 2018003946 |
| **OCLC** | 1030283001 |

The claim that *The Bitcoin Standard* by Saifedean Ammous (ISBN 9781119473862) has exactly **286 pages** is verified as correct per Open Library metadata.

---

## 4. Bitcoin.org — Irreversibility of Bitcoin Payments

**Status: ✅ CONFIRMED**

From the Bitcoin.org page ["Some things you need to know"](https://bitcoin.org/en/you-need-to-know), the following statement is explicitly documented:

> **"Bitcoin payments are irreversible."**

The full context states: *"A Bitcoin transaction cannot be reversed, it can only be refunded by the person receiving the funds."* This confirms that Bitcoin payments are irreversible by design.

---

## 5. Initial Commit — Repository History

| Field | Value |
|---|---|
| **Commit SHA** | `9b9756b931857165a008f004442362247db53f9b` |
| **Commit Message** | `Initial commit` |
| **Author** | fjcobu14 <nqflljaj554@hotmail.com> |
| **Date** | Sun Jun 14 00:42:03 2026 +0800 |
| **Added File** | `README.md` |

The repository's initial commit added only one file: **README.md**, with the commit message **"Initial commit"**.

---

## Audit Summary

| Check | Result |
|---|---|
| Total buy-side fees from Coinbase CSV | $160.59 ✅ |
| BTC buy subtotal & quantity | $10,427.40 / 0.3365580093 BTC ✅ |
| ETH buy subtotal & quantity | $17,161.24 / 10.0292379179 ETH ✅ |
| BTC/USD recognized on Binance | Confirmed ✅ |
| *The Bitcoin Standard* = 286 pages | Confirmed ✅ |
| Bitcoin payments are irreversible | Confirmed ✅ |
| Initial commit message & added file | "Initial commit" / README.md ✅ |

**All seven audit checks have been verified and confirmed.**
