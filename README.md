# g-oss-mft · Managed file transfer (SFTPGo + NiFi)

**Audience:** O&G CIOs/CTOs and integration leads  
**Goal:** Replace proprietary MFT with auditable, automated OSS for vendor file ingress.

---

## Executive summary
- **What it is:** **SFTPGo** for managed SFTP with web UI and user management. **Apache NiFi** to pull, validate, and land files into object storage (MinIO/S3) with AV scanning hooks.  
- **What it replaces:** MOVEit/GoAnywhere MFT and ad‑hoc SFTP scripts.

## Where it fits
```
[Vendor SFTP] -> SFTPGo inbox -> NiFi flow -> S3/MinIO (raw) -> dbt (standardize) -> Iceberg
```
Pairs with `g-oss-batch` for downstream standardization.

## Security & compliance
- Per‑partner credentials, IP allowlists, AV/quarantine pattern, checksum dedupe, PGP optional.  
- Full transfer logs for audit.

## KPIs for leadership
- Files processed/day, failure rate, time‑to‑land, % auto‑quarantined.

## Quick start
```bash
cp .env.example .env
docker compose up -d
# SFTPGo: http://localhost:8086  • NiFi: http://localhost:8087
```
