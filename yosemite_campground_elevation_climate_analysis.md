# Yosemite National Park Campground Elevation & Climate Analysis

> **Verified cross-referenced analysis** combining Wikipedia climate data with local NPS campground research notes.  
> Tracking Issue: [#6 – Yosemite Campground Elevation and Climate Analysis](https://github.com/fjcobu14/benchmark-test-project/issues/6)

---

## 1. Köppen Climate Classification

Per the Wikipedia article on Yosemite National Park (Climate section), Yosemite is classified as:

| Classification | Code | Description |
|---|---|---|
| **Mediterranean climate** | **Csa** | Hot-summer Mediterranean climate — most precipitation falls during mild winters; other seasons are nearly dry (less than 3% of precipitation falls during the long, hot summers) |

**Source**: Wikipedia, *Yosemite National Park* — Climate section, citing NPS/NOAA references.

---

## 2. Annual Precipitation by Elevation (Wikipedia Climate Section)

Wikipedia's Climate section explicitly states that precipitation increases with elevation due to orographic lift, up to ~8,000 ft, then slowly decreases toward the Sierra crest. The key figures:

| Elevation | Annual Precipitation | Notes |
|---|---|---|
| **4,000 ft** (1,200 m) | **36 inches** (910 mm) | Yosemite Valley / Park Headquarters level |
| **8,600 ft** (2,600 m) | **50 inches** (1,300 mm) | Tuolumne Meadows level |

**Precipitation gradient**: +14 inches (+38.9%) from 4,000 ft to 8,600 ft — a 4,600 ft elevation gain yields ~3.0 additional inches of precipitation per 1,000 ft of elevation gain.

The climate data table for Park Headquarters (elevation 4,018 ft) confirms 36.55 inches annual precipitation (1991–2020 normals), consistent with the 36-inch figure at the 4,000 ft elevation benchmark.

---

## 3. Campground Elevation Data & Median Calculation

The 10 campgrounds from `/data/yosemite_research_notes.txt` (NPS API data), sorted by elevation:

| # | Campground | Elevation (ft) | Elevation Zone |
|---|---|---|---|
| 1 | Camp 4 | 4,000 | Valley |
| 2 | Lower Pines | 4,000 | Valley |
| 3 | North Pines | 4,000 | Valley |
| 4 | Hodgdon Meadow | 4,900 | Valley |
| 5 | Crane Flat | 6,200 | Mid-elevation |
| 6 | Tamarack Flat | 6,300 | Mid-elevation |
| 7 | Bridalveil Creek | 7,200 | High elevation |
| 8 | Tuolumne Meadows | 8,000 | High elevation |
| 9 | Porcupine Flat | 8,100 | High elevation |
| 10 | Tuolumne Horse Campsites | 8,600 | High elevation |

### Computed Statistics

| Statistic | Value |
|---|---|
| **Median elevation** | **6,250 ft** (mean of 5th & 6th values: 6,200 + 6,300 / 2) |
| Mean elevation | 6,130 ft |
| Standard deviation | 1,725.72 ft |
| Minimum | 4,000 ft |
| Maximum | 8,600 ft |
| Range | 4,600 ft |

---

## 4. Elevation Zone Distribution

| Zone | Criteria | Count | Campgrounds |
|---|---|---|---|
| **Valley** | < 5,000 ft | **4** | Camp 4, Lower Pines, North Pines, Hodgdon Meadow |
| **Mid-elevation** | 5,000 – 7,000 ft | **2** | Crane Flat, Tamarack Flat |
| **High elevation** | ≥ 7,000 ft | **4** | Bridalveil Creek, Tuolumne Meadows, Porcupine Flat, Tuolumne Horse Campsites |

**Observation**: The distribution is bimodal — campgrounds cluster at valley floor (~4,000 ft) and high country (≥7,200 ft), with a thin mid-elevation band. This reflects Yosemite's geography: the dramatic valley floor and the expansive high subalpine plateaus, with fewer developed sites on the transitional slopes.

---

## 5. EPA Air Quality Index (Local Research Notes)

From the local research notes (WeatherAPI data):

| Metric | Value | Rating |
|---|---|---|
| **US EPA Index** | **1** | **Good** |
| PM2.5 | 2.1 µg/m³ | Good |
| PM10 | 2.9 µg/m³ | Good |
| CO | 110.0 µg/m³ | Good |
| O₃ | 94.0 µg/m³ | Moderate |

EPA Index **1 (Good)** indicates air quality is satisfactory and poses little or no health risk — consistent with Yosemite's wilderness designation and distance from major urban pollution sources, though ozone transport from the Central Valley remains a known concern for sequoia health (per Wikipedia ecology section).

---

## 6. Cross-Reference: Climate ↔ Campground Elevation

| Campground Elevation | Wikipedia Precipitation Estimate | Zone |
|---|---|---|
| 4,000 ft (Camp 4, Lower Pines, North Pines) | ~36 in (910 mm) | Valley — matches Park HQ data exactly |
| 4,900 ft (Hodgdon Meadow) | ~37–38 in (estimated) | Valley — slight increase from orographic lift |
| 6,200–6,300 ft (Crane Flat, Tamarack Flat) | ~42–44 in (estimated) | Mid-elevation — transitional precipitation zone |
| 7,200 ft (Bridalveil Creek) | ~47–48 in (estimated) | High — near peak precipitation belt |
| 8,000–8,600 ft (Tuolumne Meadows, Porcupine Flat, Horse Campsites) | ~49–50 in (1,300 mm) | High — matches Wikipedia's 8,600 ft figure |

**Key insight**: Campgrounds at the highest elevations (≥8,000 ft) receive nearly 40% more precipitation than valley-floor campgrounds. This has direct implications for campground seasonal accessibility — high-elevation campgrounds typically close from October through May/June due to snow accumulation, while valley campgrounds remain accessible year-round.

---

## Data Sources

| Source | Content | Verification |
|---|---|---|
| Wikipedia — *Yosemite National Park*, Climate section | Köppen classification (Csa), precipitation at 4,000 ft & 8,600 ft, temperature data | Cross-referenced with NOAA 1991–2020 normals |
| `/data/yosemite_research_notes.txt` | 10 campground elevations (NPS API), EPA air quality index, PM values | Local dataset verified against NPS descriptions |
| Computed statistics | Median, mean, std dev, zone counts | Calculated from sorted elevation array |

---

*Analysis prepared and verified on 2026-06-13.*
