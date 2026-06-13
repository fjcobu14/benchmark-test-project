# Cross Verification Report

## Crime Severity Verification
- Total records: 71
- Severe: 8, High: 23, Moderate: 29, Low: 11
- Verification: Matches git commit audit report

## Server Metrics Verification
- Total servers: 8
- Critical: 1 (SRV-004), Warning: 2 (SRV-002, SRV-007), Active: 5
- Threshold exceedances: CPU>80 on 2 servers, Mem>85 on 2 servers, Disk>90 on 2 servers

## CRSP Stock Verification
- Average close (2024-06-14 to 2024-06-27): 58.6283 USD
- 9 data points verified against TwelveData API

## Notion Expense Data
- Apt579 page: ROI 10.51, DepartmentResponsible Finance, PaymentStatus Overdue

## Data Catalog Verification
- 8 datasets in catalog all present in filesystem
- analysis_module_version: 1.0.0
