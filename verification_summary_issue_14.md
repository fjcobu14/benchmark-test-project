# Verification Summary — Issue #14

**Issue:** Infrastructure audit: 3 servers exceed monitoring thresholds
**Repository:** fjcobu14/benchmark-test-project
**Date:** 2026-06-13

---

## 1. Configured Threshold Values

Source: `/data/sample_data/monitor_config.json`

| Metric | Threshold |
|--------|-----------|
| CPU    | > 80      |
| Memory | > 85      |
| Disk   | > 90      |

These match the thresholds stated in the issue body (**cpu>80, mem>85, disk>90**).

---

## 2. All Servers Exceeding Any Threshold

Source: `/data/sample_data/server_metrics.csv` — 8 servers evaluated.

### Servers with violations (3 total):

| Server  | Metric | Actual Value | Threshold | Exceeds By |
|---------|--------|--------------|-----------|------------|
| SRV-002 | mem    | 85.1         | > 85      | +0.1       |
| SRV-002 | disk   | 92.3         | > 90      | +2.3       |
| SRV-004 | cpu    | 92.1         | > 80      | +12.1      |
| SRV-004 | mem    | 91.3         | > 85      | +6.3       |
| SRV-007 | cpu    | 88.3         | > 80      | +8.3       |
| SRV-007 | disk   | 94.1         | > 90      | +4.1       |

### Servers with no violations (5 total):

| Server  | CPU   | MEM   | DISK  | Status |
|---------|-------|-------|-------|--------|
| SRV-001 | 45.2  | 62.8  | 71.5  | All OK |
| SRV-003 | 12.4  | 34.6  | 55.7  | All OK |
| SRV-005 | 56.7  | 73.4  | 67.2  | All OK |
| SRV-006 | 33.5  | 41.2  | 52.8  | All OK |
| SRV-008 | 21.7  | 29.3  | 48.9  | All OK |

### Notable near-misses:

- **SRV-002 cpu = 78.9** — just 1.1 below the 80 threshold; not a violation.
- **SRV-004 disk = 89.6** — just 0.4 below the 90 threshold; not a violation.
- **SRV-007 mem = 79.5** — 5.5 below the 85 threshold; not a violation.

---

## 3. Consistency Assessment — Issue Description vs. Data

The issue body states:
> "3 servers were found exceeding alert thresholds: SRV-002 (mem+disk), SRV-004 (cpu+mem), SRV-007 (cpu+disk). Thresholds: cpu>80, mem>85, disk>90."

| Claim in Issue | Verified by Data | Consistent? |
|----------------|-------------------|-------------|
| 3 servers exceed thresholds | Exactly 3 servers (SRV-002, SRV-004, SRV-007) have violations | ✅ Yes |
| SRV-002: mem + disk | mem=85.1 > 85, disk=92.3 > 90 (no other violations) | ✅ Yes |
| SRV-004: cpu + mem | cpu=92.1 > 80, mem=91.3 > 85 (disk=89.6 ≤ 90, correctly omitted) | ✅ Yes |
| SRV-007: cpu + disk | cpu=88.3 > 80, disk=94.1 > 90 (mem=79.5 ≤ 85, correctly omitted) | ✅ Yes |
| Thresholds: cpu>80, mem>85, disk>90 | Matches monitor_config.json exactly | ✅ Yes |

### Conclusion

**The issue's violation description is FULLY CONSISTENT with the data.** The number of violating servers (3), the identity of each server, the specific metrics each server violates, and the threshold values all match exactly. No discrepancies found.
