# Infrastructure Threshold Violations Report

## Servers Exceeding Alert Thresholds

Based on the monitoring configuration (cpu threshold: 80%, mem threshold: 85%, disk threshold: 90%):

- SRV-002 (us-west): mem=85.1% (exceeds 85%), disk=92.3% (exceeds 90%)
- SRV-004 (ap-south): cpu=92.1% (exceeds 80%), mem=91.3% (exceeds 85%)
- SRV-007 (ap-north): cpu=88.3% (exceeds 80%), disk=94.1% (exceeds 90%)

## Summary
3 out of 8 monitored servers exceed at least one alert threshold.
Total threshold violations: 6 (2 mem, 2 cpu, 2 disk)
