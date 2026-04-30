# lab-health.py

Checks every lab service and VM. Useful after a Proxmox reboot or when troubleshooting why an alert pipeline isn't firing. Returns up/down status for all services in a few seconds.

## Usage
```bash
python3 lab_health.py
```

## Sample output
```
Lab Health Check — 2026-06-01 14:00 UTC
==================================================
✅ pfSense              UP
✅ Wazuh Dashboard      UP
✅ Velociraptor         UP
✅ n8n                  UP
✅ ElastAlert           UP
✅ DFIR-IRIS            UP
✅ Graylog              UP
✅ MISP                 UP
❌ TheHive              DOWN (ConnectionError)
✅ Security Onion       UP
```

## Requirements
```
requests>=2.28
```

## Screenshots
<!-- Add after build -->
![lab-health.py all services green](screenshots/lab-health-green.png)
![lab-health.py showing one service down](screenshots/lab-health-one-down.png)
