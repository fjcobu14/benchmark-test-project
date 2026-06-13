# Monitoring Threshold Audit Report

## Audit Summary
Based on the monitoring configuration (monitor_config.json v2.1.0) and server metrics data,
the following servers exceed the configured alert thresholds:

## Thresholds (from monitor_config.json)
- CPU: 80%
- Memory: 85%
- Disk: 90%

## Servers Exceeding Thresholds
| Server | Region | CPU | Memory | Disk | Exceeded Thresholds |
|--------|--------|-----|--------|------|--------------------|
| SRV-004 | ap-south | 92.1% | 91.3% | 89.6% | CPU, Memory |
| SRV-002 | us-west | 78.9% | 85.1% | 92.3% | Memory, Disk |
| SRV-007 | ap-north | 88.3% | 79.5% | 94.1% | CPU, Disk |

## Status Summary
- Critical: 1 server (SRV-004 exceeds both CPU and Memory thresholds)
- Warning: 2 servers (SRV-002 and SRV-007 each exceed 2 thresholds)
- Total servers exceeding at least one threshold: 3 out of 8
- Servers within all thresholds: 5 (SRV-001, SRV-003, SRV-005, SRV-006, SRV-008)