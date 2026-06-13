# Cross-Source Data Integrity Audit Report

## Verification Results

| Data Point | Source | Value | Status |
|---|---|---|---|
| Dataset count (data_sources.json) | Project config | 8 | Verified |
| Dataset count (config_verification.json) | Verification file | 8 | Matches |
| Analysis module version (data_sources.json) | Project config | 1.1.0 | Note |
| Analysis module version (config_verification.json) | Verification file | 1.0.0 | MISMATCH |
| CPU alert threshold | Monitoring config | 80% | Verified |
| Role-type entities in knowledge graph | Org knowledge base | 15 | Verified |
| Alice Gomez affiliation | Org knowledge base | BuildWell Construction | Verified |
| J.K. Rowling birth date | Open Library (OL23919A) | 31 July 1965 | Verified |
| J.K. Rowling title | Open Library (OL23919A) | OBE | Verified |
| Book cover URL (ISBN 0747532699, M) | Open Library covers | https://covers.openlibrary.org/b/isbn/0747532699-M.jpg | Verified |
| Filesystem access scope | Server config | /data | Verified |

## Inconsistencies Found

1. **Analysis module version mismatch**: data_sources.json reports version 1.1.0, but config_verification.json reports version 1.0.0. This needs investigation.
