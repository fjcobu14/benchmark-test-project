# Discrepancy Audit Report — benchmark-test-project

**Audit Date:** 2026-06-14  
**Auditor:** Automated discrepancy analysis  
**Scope:** Data catalog, configuration records, server status claims, version identifiers, and git working tree state  

---

## Executive Summary

This audit identifies **10 factual inconsistencies** across the project's data catalog, configuration records, server status claims, version identifiers, and git working tree state. The most critical discrepancies involve stale configuration metadata that no longer reflects the working tree, an incorrect server status count, and conflicting numerical analyses for the same dataset.

---

## Discrepancy #1: analysis_module_version Mismatch

| Source | Claimed Version |
|--------|----------------|
| `data_sources.json` (staged/index) | `1.0.0` |
| `data_sources.json` (working tree) | `1.1.0` |
| `config_verification.json` | `1.0.0` |
| `verification_report.txt` | `1.0.0` |

**Finding:** The `analysis_module_version` was updated from `1.0.0` to `1.1.0` in the working tree copy of `data_sources.json`, but `config_verification.json` and `verification_report.txt` still record the old version `1.0.0`. The staged (index) version also retains `1.0.0`. Three records are stale relative to the working tree.

**Severity:** Medium — version identifier inconsistency between committed/verified state and working tree.

---

## Discrepancy #2: data_sources.json File Size Mismatch

| Source | Claimed Size |
|--------|-------------|
| `config_verification.json` (`file_size_bytes`) | 332 |
| `feedback_analysis_summary.json` (`size_in_bytes`) | 332 |
| Actual working tree file size | **411 bytes** |

**Finding:** Both `config_verification.json` and `feedback_analysis_summary.json` record the file size of `data_sources.json` as 332 bytes, which matches the staged (single-line, compact JSON) version. However, the working tree version has been reformatted to multi-line JSON with additional fields, growing to 411 bytes. Both metadata records are stale.

**Severity:** Medium — configuration metadata does not reflect current file state.

---

## Discrepancy #3: data_sources.json Line Count Mismatch

| Source | Claimed Line Count |
|--------|-------------------|
| `config_verification.json` (`line_count`) | 1 |
| Actual working tree file | **16 lines** |

**Finding:** `config_verification.json` records `line_count: 1`, matching the original compact single-line JSON format. The working tree version has been reformatted to a 16-line pretty-printed JSON structure. The verified metadata is stale.

**Severity:** Low — formatting change, but metadata record is inaccurate.

---

## Discrepancy #4: Server Warning/Critical Count Understated

| Source | Claimed Count |
|--------|--------------|
| `analysis_summary.md` | "2 servers have warning or critical status" |
| `server_metrics_summary.md` | "Critical: 1, Warning: 2, Active: 5" (3 total) |
| `server_metrics.csv` (source data) | SRV-002 (warning), SRV-004 (critical), SRV-007 (warning) = **3 servers** |

**Finding:** `analysis_summary.md` claims only 2 servers have warning or critical status, but the actual CSV data and the detailed `server_metrics_summary.md` both confirm 3 such servers (1 critical + 2 warning). The summary understates the count by 1.

**Severity:** High — factual error in a key infrastructure metric summary.

---

## Discrepancy #5: SRV-007 Dual Classification in server_metrics_summary.md

| Section in server_metrics_summary.md | SRV-007 Entry |
|--------------------------------------|--------------|
| "Critical Servers" section | SRV-007 listed with "Status: warning" |
| "Warning Servers" section | SRV-007 listed with "Status: warning" |

**Finding:** SRV-007 appears under both the "Critical Servers" and "Warning Servers" section headers in `server_metrics_summary.md`. The CSV source data unambiguously classifies SRV-007 as `warning`. Its placement under "Critical Servers" is incorrect and creates an internal document contradiction (a server listed as "critical" but with its own status line saying "warning").

**Severity:** Medium — structural/logical inconsistency within a single document.

---

## Discrepancy #6: CRSP SMA/EMA Numerical Values Conflict

| Metric | `crsp_gene_editing_analysis.md` | `analysis_note.md` |
|--------|--------------------------------|--------------------|
| Average SMA | 57.5629 USD | 57.53876 USD |
| Average EMA | 58.7797 USD | 58.85615 USD |
| Average EMA−SMA difference | 1.2168 USD | 1.31739 USD |
| Data points count | **10** | **9** |

**Finding:** Two project files report different numerical averages and different data point counts for the same CRSP (CRISPR Therapeutics) 30-day SMA/EMA analysis over the same date range (2024-06-14 to 2024-06-28). The `crsp_gene_editing_analysis.md` claims 10 data points while `analysis_note.md` claims 9 trading days (explicitly noting June 19 was excluded as a US Juneteenth holiday). The numerical averages differ because of the different sample sizes used.

**Severity:** High — conflicting analytical results for the same dataset and period stored in the same repository.

---

## Discrepancy #7: Git Working Tree / Index Divergence for data_sources.json

| Aspect | Staged (Index) | Working Tree |
|--------|---------------|-------------|
| Content | Single-line compact JSON (332 bytes) | Multi-line formatted JSON (411 bytes) |
| `analysis_module_version` | `1.0.0` | `1.1.0` |
| `last_reviewed` field | Absent | Present (`"2024-06-14"`) |
| Line count | 1 | 16 |

**Finding:** `data_sources.json` has been staged as a new file (compact, v1.0.0) but subsequently modified in the working tree without re-staging. The git index and working tree are significantly diverged. Any commit based on the current index would not include the working tree changes, and any verification based on the working tree would not match what gets committed.

**Severity:** High — git state inconsistency; risk of committing stale content or losing working tree changes.

---

## Discrepancy #8: Untracked File in Working Tree

| File | Status |
|------|--------|
| `git_log_output.txt` | Untracked (not in index, not in any commit) |

**Finding:** The working directory contains `git_log_output.txt` which is untracked — it exists locally but is not part of any commit or the staging area. This file is not referenced in any project document but is present in the directory, representing an undocumented artifact.

**Severity:** Low — untracked file, no direct data inconsistency, but represents incomplete repository hygiene.

---

## Discrepancy #9: verification_report.txt Stale Claims

| Claim in verification_report.txt | Current Reality |
|---------------------------------|----------------|
| `analysis_module_version: 1.0.0` | Working tree has `1.1.0` |
| "Git diff shows data_sources.json was newly added" | Now also has unstaged modifications beyond initial addition |
| Implied: data_sources.json is unmodified since staging | Working tree has diverged from staged version |

**Finding:** The verification report describes a snapshot that no longer reflects the current state. It was accurate at the time of writing but has become stale due to subsequent working tree modifications.

**Severity:** Medium — outdated verification report could mislead future reviewers.

---

## Discrepancy #10: data_sources.json Missing `last_reviewed` in Staged Version

| Version | `last_reviewed` Field |
|---------|----------------------|
| Staged (index) | Not present |
| Working tree | `"2024-06-14"` |

**Finding:** The working tree version of `data_sources.json` introduces a new `last_reviewed` field that does not exist in the staged version. This means the committed version (if committed from the current index) would lack this field, while the local copy includes it — creating a discrepancy between what would be published and what exists locally.

**Severity:** Medium — schema inconsistency between staged and working tree versions.

---

## Discrepancy Summary Table

| # | Category | Severity | Description |
|---|----------|----------|-------------|
| 1 | Version Identifier | Medium | `analysis_module_version` 1.0.0 in config/verification vs 1.1.0 in working tree |
| 2 | Configuration Record | Medium | File size 332 in metadata vs 411 in working tree |
| 3 | Configuration Record | Low | Line count 1 in config vs 16 in working tree |
| 4 | Server Status Claim | High | analysis_summary.md claims 2 warning/critical servers; actual count is 3 |
| 5 | Server Status Claim | Medium | SRV-007 dual-listed under Critical and Warning sections |
| 6 | Data Catalog / Analysis | High | CRSP SMA/EMA values and data point counts conflict between two files |
| 7 | Git Working Tree State | High | Staged vs working tree content significantly diverged for data_sources.json |
| 8 | Git Working Tree State | Low | Untracked git_log_output.txt present but undocumented |
| 9 | Configuration Record | Medium | verification_report.txt stale — does not reflect current state |
| 10 | Version Identifier / Schema | Medium | `last_reviewed` field absent in staged version, present in working tree |

---

## JSON Files in Project Directory

The following 5 JSON files are present in `/data/repos/benchmark-test-project`:

1. **`aapl_bbands_analysis.json`** — AAPL Bollinger Bands raw indicator data (3 data points, 2025-01-06 to 2025-01-08)
2. **`aapl_bbands_summary.json`** — AAPL Bollinger Bands analysis summary metadata
3. **`config_verification.json`** — Verification metadata for data_sources.json (stale: records v1.0.0, 332 bytes, 1 line)
4. **`data_sources.json`** — Data catalog listing 8 CSV datasets (currently diverged between staged and working tree)
5. **`feedback_analysis_summary.json`** — Customer feedback complaint audit results (stale: records data_sources.json size as 332 bytes)

---

## Recommendations

1. **Re-stage data_sources.json** — Run `git add data_sources.json` to sync the index with the working tree, then update `config_verification.json` and `verification_report.txt` to reflect the new version (1.1.0), size (411 bytes), and line count (16).
2. **Correct analysis_summary.md** — Change "2 servers" to "3 servers" to match the actual CSV data.
3. **Fix server_metrics_summary.md** — Remove SRV-007 from the "Critical Servers" section; it belongs only under "Warning Servers."
4. **Reconcile CRSP analysis files** — Determine whether 9 or 10 data points is correct for the CRSP SMA/EMA analysis and update both `crsp_gene_editing_analysis.md` and `analysis_note.md` to consistent values.
5. **Remove or track git_log_output.txt** — Either delete the untracked file or add it to the repository with appropriate documentation.
6. **Update feedback_analysis_summary.json** — Correct the `size_in_bytes` field from 332 to 411 to match the current working tree state of data_sources.json.

---

*End of Discrepancy Audit Report*
