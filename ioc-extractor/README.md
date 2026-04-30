# ioc-extractor.py

Parses any text input — log files, alert output, threat reports, emails — and extracts all indicators of compromise. Private IP ranges are filtered automatically.

## Extracts
- IPv4 addresses (filters RFC1918 private ranges)
- Domains and FQDNs
- MD5, SHA1, SHA256 hashes
- URLs
- Email addresses
- CVE identifiers

## Usage
```bash
# From a file
python3 ioc_extractor.py suspicious_email.txt

# From stdin
cat wazuh_alert.json | python3 ioc_extractor.py -

# JSON output — pipe into jq for filtering
python3 ioc_extractor.py threat_report.txt --format json | jq '.ips'
```

## Sample output
```
=== IOC EXTRACTION REPORT ===
Source: suspicious_email.txt

IPs (external):       185.220.101.45, 91.108.4.0
Domains:              update-service.ru, cdn-delivery.net
Hashes (SHA256):      a3f2b1c4...
URLs:                 http://update-service.ru/payload.exe
CVEs:                 CVE-2024-1234
```

## Requirements
```
re (stdlib)
```

## Screenshots
<!-- Add after build -->
![ioc-extractor output from a threat report](screenshots/ioc-extractor-output.png)
