# Wazuh SIEM Homelab — Detection Engineering

A hands-on Wazuh SIEM lab built to practice detection engineering, custom rule writing, and MITRE ATT&CK mapping for SOC Analyst roles.

## Project Overview
This homelab simulates real-world attacks against a monitored Ubuntu target node and demonstrates how Wazuh detects them in real time. Each detection is mapped to the MITRE ATT&CK framework.

## Environment
| Component | Details |
|-----------|---------|
| Hypervisor | Proxmox VE 8.x (low-spec hardware) |
| Wazuh Server | Ubuntu Server, Wazuh 4.14.8 (All-in-One) |
| Target Node | Ubuntu Server with Wazuh Agent 4.14.8 |
| Attacker | Kali Linux (Nmap) |

## Completed Detections
| # | Attack | Rule ID | Level | MITRE Technique |
|---|--------|---------|-------|-----------------|
| 1 | Nmap Port Scan | 100101 | 8 | T1046 — Network Service Discovery |

## Detection 1 — Nmap Port Scan (T1046)
**Attack:** Ran an Nmap TCP connect scan from Kali against the target node.
**Detection:** Custom Wazuh rule correlates 15+ UFW block events from the same source IP within a 10-second window.
**Result:** Level 8 alert fired in real time, mapped to MITRE ATT&CK T1046.

* [View the Attack Write-up](attacks/nmap-scan.md)
* [View the Detection Rule](rules/local_rules.xml)

## Roadmap (Coming Soon)
- [x] Deploy Wazuh all-in-one stack
- [x] Enroll Linux agent
- [x] Detect Nmap port scan (T1046)
- [ ] Detect SSH brute force (T1110)
- [ ] Detect backdoor user creation (T1136)

## Connect
Built by **Hayan Butt** — [LinkedIn](https://www.linkedin.com/in/hayan-butt-582226296/)
Open to entry-level SOC Analyst opportunities in the UAE.
