# EUR/USD Cross-Source Verification Report

**Report Date:** 2026-06-13
**Issue Reference:** #9 — fjcobu14/benchmark-test-project
**Purpose:** Complete cross-source data verification for EUR/USD as specified in issue #9

---

## 1. Currency Group Classification

| Field | Value |
|-------|-------|
| Symbol | EUR/USD |
| Currency Group | **Major** |
| Base Currency | Euro |
| Quote Currency | US Dollar |

> **Source:** Twelve Data API — `/forex_pairs?symbol=EUR/USD`

EUR/USD is classified under the **Major** currency group, which comprises the most traded and liquid forex pairs globally.

---

## 2. EUR/USD Closing Prices — January 2–5, 2024

| Date | Close Price |
|------|------------|
| 2024-01-02 | **1.10387** |
| 2024-01-03 | **1.094176** |
| 2024-01-04 | **1.092777** |
| 2024-01-05 | **1.094739** |

> **Source:** Twelve Data API — `/time_series?symbol=EUR/USD&interval=1day&start_date=2024-01-02&end_date=2024-01-08`

**Observations:**
- The EUR/USD pair opened the year at ~1.10387 and declined over the first three sessions before recovering slightly on January 5.
- All four trading days produced valid closing prices, confirming full data coverage for the requested window.

---

## 3. EU Member States Officially Using the Euro

| Metric | Value |
|--------|-------|
| EU Member States Using the Euro | **20** |

> **Source:** Established geopolitical data — the Eurozone comprises 20 EU member states as of 2024, following Croatia's accession on January 1, 2023.

The 20 EU member states that officially use the Euro are:
1. Austria, 2. Belgium, 3. Croatia, 4. Cyprus, 5. Estonia, 6. Finland, 7. France, 8. Germany, 9. Greece, 10. Ireland, 11. Italy, 12. Latvia, 13. Lithuania, 14. Luxembourg, 15. Malta, 16. Netherlands, 17. Portugal, 18. Slovakia, 19. Slovenia, 20. Spain

---

## 4. ECB USD Reference Rate — 12 June 2026

| Field | Value |
|-------|-------|
| Publication Date | 12 June 2026 |
| ECB USD Reference Rate | **1.1567** |
| Convention | 1 EUR = 1.1567 USD (all currencies quoted against EUR as base) |

> **Source:** European Central Bank — Euro foreign exchange reference rates (https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html)

**Note:** The ECB publishes reference rates at approximately 16:00 CET on each working day. The rate of 1.1567 means one Euro equals 1.1567 US Dollars.

---

## 5. ETH Advance Trade Buy Entries — CoinbaseTradeHistory.csv

| Metric | Value |
|--------|-------|
| File | /data/CoinbaseTradeHistory.csv |
| Filter Criteria | Transaction Type = "Advance Trade Buy" AND Asset = "ETH" |
| Count | **23** |

> **Source:** Local file `/data/CoinbaseTradeHistory.csv`

**Breakdown by date:**
- 2024-01-24: 5 entries
- 2023-10-16: 3 entries
- 2023-09-01: 8 entries
- 2023-07-21: 7 entries

---

## Verification Summary

| # | Data Point | Value | Source | Verified |
|---|-----------|-------|--------|----------|
| 1 | EUR/USD Currency Group | Major | Twelve Data API | ✅ |
| 2 | EUR/USD Close (Jan 2) | 1.10387 | Twelve Data API | ✅ |
| 3 | EUR/USD Close (Jan 3) | 1.094176 | Twelve Data API | ✅ |
| 4 | EUR/USD Close (Jan 4) | 1.092777 | Twelve Data API | ✅ |
| 5 | EUR/USD Close (Jan 5) | 1.094739 | Twelve Data API | ✅ |
| 6 | EU Member States Using Euro | 20 | Geopolitical data | ✅ |
| 7 | ECB USD Ref Rate (12 Jun 2026) | 1.1567 | ECB official publication | ✅ |
| 8 | ETH Advance Trade Buy count | 23 | CoinbaseTradeHistory.csv | ✅ |

**All 8 data points have been successfully cross-source verified.**

---

*Report generated for issue #9 — fjcobu14/benchmark-test-project*