# Threshold Comparison Summary

## Monitor Config (v2.1.0) Alert Thresholds
| Metric | Threshold |
|--------|-----------|
| CPU    | 80%       |
| Memory | 85%       |
| Disk   | 90%       |

## Servers Exceeding at Least One Threshold
- SRV-004 (ap-south): exceeds CPU (92.1% > 80) and Memory (91.3% > 85)
- SRV-002 (us-west): exceeds Memory (85.1% > 85) and Disk (92.3% > 90)
- SRV-007 (ap-north): exceeds CPU (88.3% > 80) and Disk (94.1% > 90)

## Servers Within All Thresholds
- SRV-001, SRV-003, SRV-005, SRV-006, SRV-008

## Regional Alert Distribution
- ap-south: 1 server exceeding thresholds (SRV-004)
- us-west: 1 server exceeding thresholds (SRV-002)
- ap-north: 1 server exceeding thresholds (SRV-007)
- us-east, eu-central, eu-west: 0 servers exceeding thresholds