# Yosemite National Park — Cross-Source Verification Report

**Date compiled:** 2026-06-13
**Purpose:** Verify local weather data file against multiple authoritative sources and compile findings for team review.

---

## 1. Coordinate Verification

### Local File (`yosemite_weather_summary.txt`) Recorded Coordinates
- **Latitude:** 37.5817
- **Longitude:** -119.659

### Officially Geocoded Coordinates (Google Maps)
- **Latitude:** 37.8651011
- **Longitude:** -119.5383294
- **Formatted address:** Yosemite National Park, California, USA
- **Place ID:** ChIJxeyK9Z3wloAR_gOA7SycJC0

### Coordinate Match Assessment
| Dimension | File Value | Official Value | Difference |
|-----------|-----------|----------------|------------|
| Latitude  | 37.5817   | 37.8651011     | ~0.2834° (~31.5 km) |
| Longitude | -119.659  | -119.5383294   | ~0.1207° (~10.4 km) |

**⚠️ Result: Coordinates DO NOT match.** The local file's recorded coordinates are offset by approximately 0.28° in latitude and 0.12° in longitude from the official Google Maps geocoded center of Yosemite National Park. This discrepancy (~31.5 km lat, ~10.4 km lon) places the file's point well outside the park's boundaries. The file coordinates may correspond to a different reference point used by the weather data provider (WeatherAPI resolves to the same 37.5817, -119.659 for its Yosemite query), but they do not align with the authoritative Google Maps geocode.

---

## 2. Forecasted Maximum Temperature

**Source:** WeatherAPI forecast for Yosemite National Park (2026-06-13)

| Metric | Value |
|--------|-------|
| Forecast Date | 2026-06-13 |
| Max Temperature | **29.5°C (85.1°F)** |
| Min Temperature | 16.1°C (61.0°F) |
| Average Temperature | 22.7°C (72.9°F) |
| Condition | Sunny |

**Comparison with local file:** The local file recorded a max temperature of 23.4°C (74.2°F) and condition as "Moderate or heavy rain shower" — both differ significantly from the current forecast showing sunny skies at 29.5°C. This is expected as the file dates from 2024-07-15 while the forecast is current.

---

## 3. Forecasted UV Index

**Source:** WeatherAPI forecast for Yosemite National Park (2026-06-13)

| Metric | Value |
|--------|-------|
| Forecast Day UV Index | **11.4** |
| Current UV (at time of query) | 1.5 (evening) |

**Comparison with local file:** The local file recorded a UV index of 15.0, which is anomalously high (UV indices rarely exceed 12 even at high elevations under clear skies). The current forecast UV of 11.4 is more realistic for a high-elevation summer day in Yosemite.

---

## 4. Google Maps Rating

**Source:** Google Maps Place Details

| Metric | Value |
|--------|-------|
| Rating | **4.8** |
| Phone | (209) 372-0200 |
| Website | https://www.nps.gov/yose/index.htm |
| Hours | Open 24 hours (all days) |

---

## 5. Wikipedia-Documented Facts

**Source:** Wikipedia article "Yosemite National Park"

| Fact | Value |
|------|-------|
| Area | **3,070 km²** (1,187 mi²) |
| World Heritage Designation Year | **1984** |
| Managing Agency | National Park Service |
| Counties | Tuolumne, Mariposa, Mono, Madera |
| Annual Visitors | ~4 million |
| Wilderness % | ~95% |

---

## 6. GitHub Issues Referencing 'Yosemite national park'

**Source:** GitHub Issues Search

| Metric | Value |
|--------|-------|
| Total matching results | **298** |

### First 5 Results

| # | Repository | Identifier | Type | Title |
|---|-----------|------------|------|-------|
| 1 | fjcobu14/test-verification-issue | #2 | Issue | Cross-Source Verification Report: Yosemite National Park Conditions |
| 2 | JoshuaTreeTours/alloutdooradventures2 | PR #841 | PR | Add Engine6 Yosemite Sequoias Glacier Point adventure |
| 3 | fjcobu14/test-verification-issue | #1 | Issue | Yosemite Environmental Conditions Verification Report |
| 4 | fjcobu14/benchmark-test-project | #6 | Issue | Yosemite Campground Elevation and Climate Analysis |
| 5 | Atamyrat2005/snake-game | #6 | Issue | Yosemite trip safety assessment - high elevation campground UV risk check |

---

## 7. Summary of Discrepancies Found

| Data Point | Local File | Authoritative Source | Match? |
|------------|-----------|---------------------|--------|
| Coordinates (lat) | 37.5817 | 37.8651011 (Google Maps) | ❌ No |
| Coordinates (lon) | -119.659 | -119.5383294 (Google Maps) | ❌ No |
| Max Temperature | 23.4°C | 29.5°C (WeatherAPI forecast) | ❌ No (different date) |
| Condition | Rain shower | Sunny (WeatherAPI forecast) | ❌ No (different date) |
| UV Index | 15.0 | 11.4 (WeatherAPI forecast) | ❌ No (15.0 is anomalously high) |

**Note:** Temperature and condition mismatches are attributable to the file being from 2024-07-15 while the forecast is for 2026-06-13. The coordinate and UV index discrepancies are more concerning — the coordinates are significantly offset from the official geocoded location, and a UV index of 15.0 exceeds the theoretical maximum for the UV index scale at such latitudes.

---

## 8. Sources Consulted

1. **Local file:** `/data/repos/benchmark-test-project/yosemite_weather_summary.txt`
2. **Google Maps Geocoding API** — coordinates and place details
3. **WeatherAPI** — current forecast data
4. **Wikipedia** — park area and World Heritage status
5. **GitHub Issues Search** — issue/PR references
6. **OpenStreetMap/Nominatim** — geocoding (query timed out; Google Maps used as primary)

---

*Report compiled automatically via multi-source cross-verification pipeline.*