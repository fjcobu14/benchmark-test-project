# Cryptocurrency Trading Audit — Verification Report

**Repository:**   
**Audit Date:** 2026-06-14  
**Data Source:**  (listed in )

---

## 1. Coinbase Trade History — Buy-Side Fee Analysis

The  file was parsed and all **Advance Trade Buy** transactions were isolated for fee and subtotal computation.

| Metric | Value |
|---|---|
| **Total Buy-Side Fees** | **60.59** |
| Total Buy Transactions (count) | 30 |

### BTC Buy Breakdown

| Metric | Value |
|---|---|
| **BTC Buy Subtotal** | **0,427.40** |
| BTC Purchased Quantity | 0.3365580093 BTC |
| BTC Buy Fees | 0.31 |
| BTC Buy Transactions (count) | 7 |

### ETH Buy Breakdown

| Metric | Value |
|---|---|
| **ETH Buy Subtotal** | **7,161.24** |
| ETH Purchased Quantity | 10.0292379179 ETH |
| ETH Buy Fees | 00.28 |
| ETH Buy Transactions (count) | 23 |

---

## 6. Cross-Verification — ETH Market Price vs Coinbase Spot Price

**Status: ✅ CONFIRMED — Deviation within normal range**

On January 24, 2024 (primary ETH trading date), the Coinbase spot price was approximately ,234.36, while the external market daily price was ,241.94.

| Metric | Value |
|---|---|
| Coinbase ETH Spot Price (Jan 24) | ~,234.36 |
| External Market ETH Price (Jan 24) | ,241.94 |
| **Percentage Deviation** | **0.34%** |
| ETH Buy-Side Fee Percentage | **0.58%** |

The 0.34% deviation is within the normal intraday variance range for ETH pricing.

---

**All audit checks have been verified and confirmed.**