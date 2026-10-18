# Custom Wazuh Rules

This folder contains all custom detection rules written for the homelab.

## Rule Reference
| Rule ID | Description | Level | MITRE |
|---------|-------------|-------|-------|
| 100100 | UFW block (base rule) | 3 | — |
| 100101 | Nmap port scan detection | 8 | T1046 |

## Rule 100101 — Nmap Port Scan
**Logic:** Correlates 15+ UFW block events from the same source IP within 10 seconds.

**Why it works:** A normal user connection rarely generates 15 blocked attempts in 10 seconds. An Nmap scan does this immediately.

**Tested with:** `nmap -sT -p 1-1000 -T4 --min-rate 500 <target>`

## How to Deploy
1. Copy `local_rules.xml` to `/var/ossec/etc/rules/` on the Wazuh Manager.
2. Restart the manager: `sudo systemctl restart wazuh-manager`
3. Test with: `sudo /var/ossec/bin/wazuh-logtest`
