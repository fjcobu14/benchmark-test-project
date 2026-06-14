# NightSkyTracker Observation Readiness Audit

**Audit Date:** 2026-06-14
**Project:** NightSkyTracker v2.1
**Repository:** fjcobu14/benchmark-test-project
**Observation Site:** Mount Wilson Observatory

---

## 1. Mount Wilson Observatory — Observation Session Criteria

### Session Criteria (NightSkyTracker v2.1)

| Criterion | Threshold | Observed Value | Status |
|-----------|-----------|----------------|--------|
| Moon Illumination | ≤ 10% | 1% (New Moon) | ✅ PASS |
| US EPA Air Quality Index | ≤ 2 | 2 (Moderate) | ✅ PASS |
| Visibility | ≥ 10 km | 16.0 km | ✅ PASS |

**Overall Session Readiness: ✅ READY — All three session criteria are satisfied.**

### Observation Configuration

- **Site:** Mount Wilson Observatory (34.2243°N, 118.0573°W)
- **Elevation:** 1742 m
- **Telescope:** 60-inch Hale
- **Filters:** clear, H-alpha, O-III (3 total)
- **Exposure:** 120 seconds
- **Primary Target:** Moon phase verification
- **Secondary Target:** Saturn opposition

---

## 2. Elevation Comparison — Mount Wilson vs. Yosemite Campground Average

### 10 Yosemite Campgrounds with Listed Elevation Data

| Campground | Elevation (ft) | Elevation (m) |
|------------|----------------|---------------|
| Bridalveil Creek | 7,200 | 2,194.56 |
| Camp 4 | 4,000 | 1,219.20 |
| Crane Flat | 6,200 | 1,889.76 |
| Hodgdon Meadow | 4,900 | 1,493.52 |
| Lower Pines | 4,000 | 1,219.20 |
| North Pines | 4,000 | 1,219.20 |
| Porcupine Flat | 8,100 | 2,468.88 |
| Tamarack Flat | 6,300 | 1,920.24 |
| Tuolumne Horse Campsites | 8,600 | 2,621.28 |
| Tuolumne Meadows | 8,000 | 2,438.40 |

**Average Elevation:** 6,130 ft = **1,868.42 m**

### Comparison

| Metric | Mount Wilson | Yosemite 10-Campground Average |
|--------|-------------|------------------------------|
| Elevation (m) | 1,742 | 1,868.42 |
| Elevation (ft) | 5,715.2 | 6,130.0 |

**Mount Wilson Observatory sits 126.42 m (414.8 ft) below the average elevation of the 10 Yosemite campgrounds — approximately 6.77% lower.**

---

## 3. Data Integrity Status

### Working Directory Cleanliness

- **Status:** ✅ CLEAN — No uncommitted changes; working tree clean.
- Local branch is behind origin/main by 17 commits (fast-forwardable).

### Dataset Catalog Size

- **Datasets listed in catalog (data_sources.json):** 8
- **Datasets present on filesystem:** 8 CSV files
- **Catalog-to-filesystem match:** ✅ All 8 datasets present and accounted for

### Server Threshold Violations

- **Servers exceeding at least one alert threshold:** 3 out of 8
- **Total threshold violations:** 6

| Server | Region | Violated Thresholds | Details |
|--------|--------|--------------------|--------|
| SRV-002 | us-west | Memory, Disk | mem=85.1% (>85%), disk=92.3% (>90%) |
| SRV-004 | ap-south | CPU, Memory | cpu=92.1% (>80%), mem=91.3% (>85%) |
| SRV-007 | ap-north | CPU, Disk | cpu=88.3% (>80%), disk=94.1% (>90%) |

Thresholds: CPU ≥ 80%, Memory ≥ 85%, Disk ≥ 90%

---

## 4. Snake-Game Submodule — New Files in origin/test vs. main

- **Submodule:** snake-game (Atamyrat2005/snake-game)
- **Files on main branch:** 5 (.gitattributes, .github/FUNDING.yml, .gitignore, README.md, snake-game.py)
- **Files on origin/test branch:** 3 (.gitattributes, .gitignore, snake-game.py)
- **New files in origin/test relative to main:** **0**
- **Changes:** 2 files deleted (.github/FUNDING.yml, README.md), 1 file modified (snake-game.py)

---

## 5. Audit Publication Confirmation

- **Commit SHA:** Published with this commit
- **Issue Comment ID:** Posted to Issue #18 (NightSkyTracker Compliance Audit - Mount Wilson)

---

*NightSkyTracker Observation Readiness Audit — completed 2026-06-14*