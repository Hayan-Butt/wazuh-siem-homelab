# Attack Write-up: Nmap Port Scan (T1046)

## Objective
Simulate network reconnaissance against the target node and verify Wazuh detects the activity.

## Execution
**Tool used:** Nmap (from Kali Linux)
**Command:**
```bash
nmap -sT -p 1-1000 -T4 --min-rate 500 <ip>
