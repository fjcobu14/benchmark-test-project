# Cross-Source Data Integrity Audit Report

**Project**: fjcobu14/benchmark-test-project  
**Date**: 2026-06-13  
**Auditor**: Automated cross-source reconciliation  

---

## Executive Summary

This audit reconciles data across four distinct sources: project configuration files (`data_sources.json`, `config_verification.json`), monitoring settings (`monitor_config.json`), the organizational knowledge graph, and Open Library records. **One inconsistency was identified** — a version mismatch in the `analysis_module_version` field between the two configuration files. All other cross-source data points are verified and consistent.

---

## 1. Dataset Count Consistency ✅ CONSISTENT

| Source | Value | Detail |
|--------|-------|--------|
| `data_sources.json` | 8 datasets | Explicit array listing: Barber Shop.csv, CoinbaseTradeHistory.csv, Covid 19 impacts on hospitals.csv, Crime_records.csv, Pet Care 2023 Weekly Financials.csv, Top Movies.csv, fantasy sports.csv, food and beverage consumption.csv |
| `config_verification.json` | 8 (`dataset_count: 8`) | Declared count field |

**Finding**: Both sources agree on a count of **8 datasets**. The dataset count is **consistent** across configuration files.

---

## 2. Analysis Module Version ❌ INCONSISTENCY

| Source | Value |
|--------|-------|
| `data_sources.json` | `analysis_module_version: "1.1.0"` |
| `config_verification.json` | `analysis_module_version: "1.0.0"` |

**Finding**: **Mismatch detected**. `data_sources.json` references version **1.1.0** while `config_verification.json` references version **1.0.0**. This discrepancy suggests either:
- `config_verification.json` was generated against an older module version and not updated, or
- `data_sources.json` was updated to reflect a newer version without corresponding verification metadata.

**Recommendation**: Determine which version is authoritative and update both files to reflect the same `analysis_module_version`.

---

## 3. CPU Alert Threshold

| Source | Field | Value |
|--------|-------|-------|
| `/data/sample_data/monitor_config.json` | `alert_thresholds.cpu` | **80** (percent) |

Additional thresholds documented for context:
- Memory (`mem`): 85%
- Disk (`disk`): 90%
- Monitoring interval: 60 seconds
- Config version: 2.1.0

---

## 4. Role-Type Entities in Organizational Knowledge

**Search query**: `"role"`  
**Result**: **15 Role-type entities** returned

| # | Role Name | Key Observations |
|---|-----------|------------------|
| 1 | Project Manager | Oversees project execution; Coordinates cross-functional teams |
| 2 | Site Engineer | Monitors structural integrity; Implements design plans |
| 3 | Electrician | Installs and tests electrical systems; Ensures power safety |
| 4 | Plumber | Manages water and sewage systems; Performs pipe installations |
| 5 | Safety Officer | Conducts safety audits; Trains crew on compliance |
| 6 | Student | Enrolled in educational institution; Completes coursework |
| 7 | Accountant | Manages financial records; Prepares tax filings |
| 8 | University Student | Studies engineering curriculum; Engages in research |
| 9 | Chef | Develops menus; Supervises kitchen operations |
| 10 | Lawyer | Provides legal counsel; Drafts contracts |
| 11 | Bank Manager | Oversees branch operations; Manages client relations |
| 12 | Retired Principal | Led school administration; Mentors new educators |
| 13 | Civil Engineer | Designs infrastructure projects; Conducts site analysis |
| 14 | Artist | Creates visual artwork; Exhibits in galleries |
| 15 | Doctor | Diagnoses conditions; Provides patient care |

---

## 5. Alice Gomez Affiliation

**Entity**: Alice Gomez (Person)  
**Affiliated Organization**: **BuildWell Construction** (Organization)  

| Entity | Type | Key Observations |
|--------|------|------------------|
| Alice Gomez | Person | Leads multi-team construction projects; Coordinates client deliverables; 8 years of field experience; Certified PMP |
| BuildWell Construction | Organization | Top-tier residential contractor; Specializes in home renovations |

The affiliation is consistent: Alice Gomez's construction project leadership role aligns with BuildWell Construction's residential contracting focus.

---

## 6. J.K. Rowling — Open Library Author Record

**Open Library Author Key**: OL23919A  

| Field | Value |
|-------|-------|
| Birth date | **31 July 1965** |
| Title | **OBE** (Order of the British Empire) |
| Fuller name | Joanne "Jo" Rowling |
| Personal name | J. K. Rowling |
| Notable alternate names | Robert Galbraith, Newt Scamander, Kennethilworthy Whisp |
| VIAF ID | 116796842 |
| Wikidata ID | Q34660 |

---

## 7. Book Cover Image URL

**ISBN**: 0747532699  
**Size**: Medium (M)  
**URL**: `https://covers.openlibrary.org/b/isbn/0747532699-M.jpg`

---

## 8. Filesystem Server Allowed Directory

**Sole allowed directory**: `/data`

The filesystem server is configured to access only the `/data` directory and its subdirectories.

---

## Inconsistency Summary

| # | Field | Source A | Source B | Status |
|---|-------|----------|----------|--------|
| 1 | Dataset count | data_sources.json (8) | config_verification.json (8) | ✅ Consistent |
| 2 | analysis_module_version | data_sources.json ("1.1.0") | config_verification.json ("1.0.0") | ❌ **Mismatch** |

**Total inconsistencies found: 1**  
**Total consistent cross-source verifications: 1**  

---

## Recommendations

1. **Resolve version mismatch**: Update `config_verification.json` to reflect `analysis_module_version: "1.1.0"` (or downgrade `data_sources.json` to `1.0.0`) to ensure configuration consistency.
2. **Add explicit affiliation relations**: The knowledge graph should store an explicit `affiliated_with` relation between Alice Gomez and BuildWell Construction for clearer data integrity.
3. **Periodic reconciliation**: Schedule regular cross-source audits to catch configuration drift early.

---

*Report generated as part of cross-source data integrity audit for benchmark-test-project.*