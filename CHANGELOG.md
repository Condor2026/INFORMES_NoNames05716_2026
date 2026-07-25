# Changelog

## [1.0.0] - 2026-07-25

### Added
- Initial repository structure (`/reports`, `/iocs`, `/telemetry`, `/tools`).
- Comprehensive threat intelligence report on NoName057(16).
- Primary IP mapping: `45.154.98.101` (AS210558 - NL).
- IoCs: 150+ `sslip.io` subdomains, 22 `d3d97e...com` subdomains, 93 Excel droppers.
- Main payload hashes: `bb01...` (Emotet) and `3b215...` (Excel dropper).
- Andromeda telemetry: 11,765 sightings, 24,484 active botnet IPs.
- MITRE ATT&CK mapping (T1566, T1204, T1027, T1568, T1046, T1071, T1498).
- YARA rules references for Emotet detection.

### Security
- Added `SECURITY.md` for responsible disclosure.
- Added `DISCLAIMER.md` for legal and ethical use.
