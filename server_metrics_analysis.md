# Server Metrics Analysis

## Monitoring Configuration
- **Monitoring Interval**: 60 seconds
- **Version**: 2.1.0
- **Regions**: us-east, us-west, eu-central, eu-west, ap-south, ap-north

## Alert Thresholds
- **CPU**: 80%
- **Memory**: 85%
- **Disk**: 90%

## Server Status Summary
| Server ID | CPU | Memory | Disk | Status | Region | Exceeds Threshold? |
|-----------|-----|--------|------|--------|--------|--------------------|
| SRV-001 | 45.2 | 62.8 | 71.5 | active | us-east | No |
| SRV-002 | 78.9 | 85.1 | 92.3 | warning | us-west | Yes (mem + disk) |
| SRV-003 | 12.4 | 34.6 | 55.7 | active | eu-central | No |
| SRV-004 | 92.1 | 91.3 | 89.6 | critical | ap-south | Yes (cpu + mem) |
| SRV-005 | 56.7 | 73.4 | 67.2 | active | us-east | No |
| SRV-006 | 33.5 | 41.2 | 52.8 | active | eu-west | No |
| SRV-007 | 88.3 | 79.5 | 94.1 | warning | ap-north | Yes (cpu + disk) |
| SRV-008 | 21.7 | 29.3 | 48.9 | active | us-west | No |

## Servers Exceeding Thresholds
- SRV-002: memory 85.1 > 85, disk 92.3 > 90
- SRV-004: cpu 92.1 > 80, memory 91.3 > 85
- SRV-007: cpu 88.3 > 80, disk 94.1 > 90

3 of 8 servers exceed at least one alert threshold.
