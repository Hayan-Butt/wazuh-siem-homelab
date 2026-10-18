# Custom Wazuh Rules

This folder contains all custom detection rules written for the homelab.

## Rule Reference

| Rule ID | Description | Level | MITRE |
|---------|-------------|-------|-------|
| 100100 | UFW block (base rule) | 3 | — |
| 100101 | Nmap port scan detection | 8 | T1046 |
| 100102 | SSH brute force detection | 10 | T1110 |
| 100103 | Backdoor user creation | 12 | T1136 |

## Rule 100101 — Nmap Port Scan

**Logic:** Correlates 15+ UFW block events from the same source IP within 10 seconds.

**Why it works:** A normal user connection rarely generates 15 blocked attempts in 10 seconds. An Nmap scan does this immediately.

**Tested with:** `nmap -sT -p 1-1000 -T4 --min-rate 500 <target>`

## Rule 100102 — SSH Brute Force

**Logic:** Correlates 8+ SSH authentication failures within 120 seconds.

**Why it works:** Legitimate users occasionally mistype passwords, but 8 failures in 2 minutes indicates automated brute force.

## Rule 100103 — Backdoor User Creation

**Logic:** Triggers on file integrity monitoring (FIM) changes to `/etc/passwd`.

**Why it works:** Any new user on the system modifies `/etc/passwd`. Real-time FIM catches this the instant it happens.

## How to Deploy

1. Copy `local_rules.xml` to `/var/ossec/etc/rules/` on the Wazuh Manager
2. Restart the manager: `sudo systemctl restart wazuh-manager`
3. Test with: `sudo /var/ossec/bin/wazuh-logtest`
