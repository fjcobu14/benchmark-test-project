# Verified Benchmark Data Points

## Context

This document records five cross-verified data points for the computational biology lab's reference database for protein structure prediction methods. Background context is drawn from the Wikipedia article on **AlphaFold**, an AI program developed by DeepMind (Alphabet subsidiary) that performs protein structure predictions. AlphaFold 2 achieved a transformational result at CASP14 (2020), scoring above 90 on the GDT for approximately two-thirds of proteins, and its paper (published in *Nature*, 2021) has been cited nearly 43,000 times. AlphaFold 3 (announced May 2024) extended predictions to protein complexes with DNA, RNA, ligands, and ions, showing at minimum 50% improvement in accuracy for protein–other-molecule interactions over existing methods. The 2024 Nobel Prize in Chemistry was shared by Demis Hassabis and John Jumper for protein structure prediction, and David Baker for computational protein design. Despite these advances, the protein folding problem remains unsolved, and roughly one-third of AlphaFold 2 predictions still lack sufficient accuracy — underscoring the ongoing challenge that benchmark databases like this one aim to address.

---

## Data Point 1 — Journal for PubMed ID 42287093

**Verified Value:** `IUBMB life`

- Source: PubMed metadata API (PMID 42287093)
- Article title: "Single-Sequence Deep Learning Delivers Crystal-Quality Models of Covalent K-Ras G12 Hotspot Complexes"

---

## Data Point 2 — First Author of PubMed ID 42287093

**Verified Value:** `Jung`

- Source: PubMed metadata API (PMID 42287093)
- Full author list: Jung, Zheng, Shokat

---

## Data Point 3 — Number of PubMed Search Results for 'protein structure prediction' (max 5 requested)

**Verified Value:** `3`

- Source: PubMed keyword search API, query term "protein structure prediction", num_results=5
- The search returned 3 results (fewer than the requested maximum of 5)

---

## Data Point 4 — Average Campground Elevation (feet)

**Verified Value:** `6,130 ft`

- Source: `/data/yosemite_research_notes.txt`
- Based on 10 Yosemite campgrounds with recorded elevations ranging from 4,000 ft to 8,600 ft

---

## Data Point 5 — PM2.5 Concentration (ug/m3)

**Verified Value:** `2.1 ug/m3`

- Source: `/data/yosemite_research_notes.txt` (Air Quality section, from WeatherAPI)
- US EPA Index: 1 (Good)

---

## Summary Table

| # | Data Point | Verified Value | Source |
|---|-----------|---------------|--------|
| 1 | Journal (PMID 42287093) | IUBMB life | PubMed metadata |
| 2 | First Author (PMID 42287093) | Jung | PubMed metadata |
| 3 | PubMed results for 'protein structure prediction' (max 5) | 3 | PubMed search |
| 4 | Average campground elevation | 6,130 ft | yosemite_research_notes.txt |
| 5 | PM2.5 concentration | 2.1 ug/m3 | yosemite_research_notes.txt |
