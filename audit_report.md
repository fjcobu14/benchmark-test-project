# Comprehensive Data Audit Report

## Verification 1: Dataset Presence Check

The `data_sources.json` file lists 8 datasets:

| # | Dataset Name | Present in /data? |
|---|---|---|
| 1 | Barber Shop.csv | ✅ Yes |
| 2 | CoinbaseTradeHistory.csv | ✅ Yes |
| 3 | Covid 19 impacts on hospitals.csv | ✅ Yes |
| 4 | Crime_records.csv | ✅ Yes |
| 5 | Pet Care 2023 Weekly Financials.csv | ✅ Yes |
| 6 | Top Movies.csv | ✅ Yes |
| 7 | fantasy sports.csv | ✅ Yes |
| 8 | food and beverage consumption.csv | ✅ Yes |

**Result: 8 out of 8 datasets listed in data_sources.json are present in the /data directory (100% match).**

## Verification 2: Crime Records Analysis

From `Crime_records.csv`:

- **Total record count**: 71
- **Arrest rate**: 59.15% (42 records where Arrest_Made = 'Yes' out of 71 total)
- **Most frequent Crime_Severity category**: Moderate (29 records)

Severity distribution: Moderate (29), High (23), Low (11), Severe (8)

## Verification 3: Yosemite Campground Elevation Verification

The `yosemite_research_notes.txt` states an average elevation of 6,130 ft for 10 listed campgrounds. Individual elevation values:

| Campground | Elevation (ft) |
|---|---|
| Bridalveil Creek Campground | 7,200 |
| Camp 4 Campground | 4,000 |
| Crane Flat Campground | 6,200 |
| Hodgdon Meadow Campground | 4,900 |
| Lower Pines Campground | 4,000 |
| North Pines Campground | 4,000 |
| Porcupine Flat Campground | 8,100 |
| Tamarack Flat Campground | 6,300 |
| Tuolumne Horse Campsites | 8,600 |
| Tuolumne Meadows Campground | 8,000 |

Computed arithmetic mean: (7200 + 4000 + 6200 + 4900 + 4000 + 4000 + 8100 + 6300 + 8600 + 8000) / 10 = 61,300 / 10 = **6,130.0 ft**

**Result: The stated average elevation of 6,130 ft matches the computed arithmetic mean of 6,130.0 ft. ✅ Confirmed.**

## Verification 4: Open Issues Count

The repository has **2 open issues**:

- Issue #1: "Feature: Add data analysis module"
- Issue #2: "Audit: Verify financial records and neighborhood school facilities for Apt579 area"

## Verification 5: NPS Yosemite Webpage Confirmation

The official NPS Yosemite webpage (https://www.nps.gov/yose/) confirms the park description:

> "Not just a great valley, but a shrine to human foresight, the strength of granite, the power of glaciers, the persistence of life, and the tranquility of the High Sierra. First protected in 1864, Yosemite National Park is best known for its waterfalls, but within its nearly 1,200 square miles, you can find deep valleys, grand meadows, ancient giant sequoias, a vast wilderness area, and much more."

**Result: The official NPS Yosemite webpage confirms the park description. ✅ Verified.**

---

## Audit Summary

| Verification | Result |
|---|---|
| 1. Dataset presence | 8/8 datasets present (100%) |
| 2. Crime records | 71 records, 59.15% arrest rate, Moderate is most frequent severity |
| 3. Yosemite elevation | Stated 6,130 ft matches computed mean of 6,130.0 ft ✅ |
| 4. Open issues | 2 open issues |
| 5. NPS webpage | Park description confirmed ✅ |
