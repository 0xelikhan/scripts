# alert-enricher.py

Takes a Wazuh alert, enriches it with VirusTotal reputation data and GeoIP context, and outputs a formatted incident report. Turns a raw SIEM alert into something ready to paste into a case.

## What it does
1. Pulls the latest high-severity alert from the Wazuh API
2. Extracts all IPs and hashes from the alert
3. Queries VirusTotal for reputation on each indicator
4. Queries GeoIP for location context on external IPs
5. Outputs a formatted incident report to stdout or file

## Usage
```bash
python3 alert_enricher.py \
  --wazuh-ip 10.10.10.10 \
  --wazuh-pass YOUR_PASSWORD \
  --vt-key YOUR_VT_API_KEY \
  --output report.txt
```

## Sample output
```
INCIDENT REPORT — 2026-06-01 14:32 UTC
Alert: Possible LSASS Credential Dumping (Rule 100001)
Agent: win11-victim (10.10.20.20)

INDICATORS
  IP: 10.10.30.45 — Kali attacker, Orlando FL (internal)
  Hash: a3f2... — VT: 47/72 detections — Mimikatz

RECOMMENDED ACTION
  Isolate win11-victim, collect memory image via Velociraptor
```

## Requirements
```
requests>=2.28
```

## Screenshots
<!-- Add after build -->
![alert_enricher.py output showing enriched report](screenshots/alert-enricher-output.png)
