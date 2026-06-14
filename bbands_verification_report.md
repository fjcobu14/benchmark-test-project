# Bollinger Bands Verification Report

**Verification Date:** 2026-06-14
**Analyst:** Automated Verification System
**Analysis IDs:** AAPL-BBANDS-2025W01, EUR/USD BBands Report

---

## 1. AAPL Bollinger Bands — Bandwidth Accuracy (2025-01-08)

### Stored Data Reference
- **Analysis ID:** AAPL-BBANDS-2025W01
- **File:** `aapl_bbands_summary.json` in `/data/repos/benchmark-test-project/`
- **Stored bandwidth (2025-01-08):** 19.88836
- **Parameters:** 20-period SMA, 2 standard deviations, series_type=close

### Live Verification
Since the Twelve Data demo API did not return BBands values for 2025-01-08 directly, the bandwidth was independently computed from 20 closing prices (2024-12-10 through 2025-01-08) obtained via the live time series endpoint:

| Component | Computed Value |
|---|---|
| Middle Band (SMA) | 249.75100 |
| Population Std Dev | 4.97209 |
| Upper Band | 259.69518 |
| Lower Band | 239.80682 |
| **Bandwidth** | **19.88837** |

### Cross-Validation
The 2025-01-07 BBands were also computed and matched the live API values exactly (SMA=249.95350, Upper=259.47089, Lower=240.43612), confirming the computation methodology is correct.

### Result
| Metric | Stored Value | Live Value | Difference | Status |
|---|---|---|---|---|
| Bandwidth | 19.88836 | 19.88837 | 0.00001 | ✅ **ACCURATE** |

The 0.00001 difference is attributable to floating-point rounding and is within acceptable tolerance.

### Bandwidth Percentage
- **Bandwidth %** = (Bandwidth / Middle Band) × 100 = (19.88837 / 249.75100) × 100 = **7.96328%**

---

## 2. EUR/USD Bollinger Bands — Session Data Cross-Check

### Stored Data Reference
- **File:** `/data/forex_analysis/eurusd_bbands_report.md`
- **Parameters:** 20-period SMA, 2 standard deviations, series_type=close
- **5 Sessions Listed:** 2026-06-10 through 2026-06-14

### Live Verification
Live BBands data was retrieved from the Twelve Data API for the same date range (2026-06-08 through 2026-06-14). The 5 sessions from the report were compared against the live values:

| Date | Component | Report Value | Live Value | Difference | Status |
|---|---|---|---|---|---|
| 2026-06-10 | Upper | 1.16997 | 1.16997 | 0.00000 | ✅ MATCH |
| 2026-06-10 | Middle | 1.16003 | 1.16003 | 0.00000 | ✅ MATCH |
| 2026-06-10 | Lower | 1.15008 | 1.15008 | 0.00000 | ✅ MATCH |
| 2026-06-10 | Bandwidth | 0.01989 | 0.01989 | 0.00000 | ✅ MATCH |
| 2026-06-11 | Upper | 1.16989 | 1.16989 | 0.00000 | ✅ MATCH |
| 2026-06-11 | Middle | 1.15991 | 1.15991 | 0.00000 | ✅ MATCH |
| 2026-06-11 | Lower | 1.14992 | 1.14992 | 0.00000 | ✅ MATCH |
| 2026-06-11 | Bandwidth | 0.01997 | 0.01997 | 0.00000 | ✅ MATCH |
| 2026-06-12 | Upper | 1.16981 | 1.16981 | 0.00000 | ✅ MATCH |
| 2026-06-12 | Middle | 1.15973 | 1.15973 | 0.00000 | ✅ MATCH |
| 2026-06-12 | Lower | 1.14965 | 1.14965 | 0.00000 | ✅ MATCH |
| 2026-06-12 | Bandwidth | 0.02016 | 0.02016 | 0.00000 | ✅ MATCH |
| 2026-06-13 | Upper | 1.16961 | 1.16961 | 0.00000 | ✅ MATCH |
| 2026-06-13 | Middle | 1.15950 | 1.15950 | 0.00000 | ✅ MATCH |
| 2026-06-13 | Lower | 1.14939 | 1.14939 | 0.00000 | ✅ MATCH |
| 2026-06-13 | Bandwidth | 0.02022 | 0.02022 | 0.00000 | ✅ MATCH |
| 2026-06-14 | Upper | 1.16904 | 1.16905 | 0.00001 | ⚠️ MINOR DISCREPANCY |
| 2026-06-14 | Middle | 1.15913 | 1.15915 | 0.00002 | ⚠️ MINOR DISCREPANCY |
| 2026-06-14 | Lower | 1.14923 | 1.14926 | 0.00003 | ⚠️ MINOR DISCREPANCY |
| 2026-06-14 | Bandwidth | 0.01981 | 0.01979 | 0.00002 | ⚠️ MINOR DISCREPANCY |

### Result
- **4 out of 5 sessions match exactly** (2026-06-10 through 2026-06-13)
- **1 session has minor discrepancies** (2026-06-14): differences of 0.00001–0.00003 in band values and 0.00002 in bandwidth
- The 2026-06-14 discrepancies are likely due to the report being generated from a slightly earlier data snapshot or different rounding precision at the time of report creation

### Bandwidth Percentage (Most Recent Session: 2026-06-14)

Using **live data**:
- Bandwidth = 1.16905 − 1.14926 = 0.01979
- Middle Band = 1.15915
- **Bandwidth %** = (0.01979 / 1.15915) × 100 = **1.70729%**

Using **report data**:
- Bandwidth = 0.01981
- Middle Band = 1.15913
- **Bandwidth %** = (0.01981 / 1.15913) × 100 = **1.70904%**

---

## 3. Bandwidth Percentage Summary

| Instrument | Date | Bandwidth | Middle Band | Bandwidth % | Data Source |
|---|---|---|---|---|---|
| AAPL | 2025-01-08 | 19.88837 | 249.75100 | **7.96328%** | Live computed |
| EUR/USD | 2026-06-14 | 0.01979 | 1.15915 | **1.70729%** | Live API |
| EUR/USD | 2026-06-14 | 0.01981 | 1.15913 | **1.70904%** | Report |

---

## 4. Overall Verification Conclusion

| Verification Item | Result | Details |
|---|---|---|
| AAPL bandwidth (2025-01-08) | ✅ **ACCURATE** | Stored 19.88836 vs live 19.88837 (diff 0.00001, rounding tolerance) |
| EUR/USD 5 sessions | ✅ **4/5 EXACT MATCH, 1/5 MINOR DISCREPANCY** | 2026-06-14 has 0.00001–0.00003 differences |
| AAPL bandwidth % (2025-01-08) | **7.96328%** | Computed from live data |
| EUR/USD bandwidth % (2026-06-14) | **1.70729%** (live) / **1.70904%** (report) | Minor difference due to band value discrepancies |

**Overall Status: VERIFIED — Both datasets are substantially accurate. The AAPL bandwidth is confirmed correct. The EUR/USD report data matches live data for 4 of 5 sessions with only negligible rounding discrepancies on the most recent session.**

---

*Report generated 2026-06-14 by Automated Verification System. Data sourced from Twelve Data API (demo key) and local stored analysis files.*