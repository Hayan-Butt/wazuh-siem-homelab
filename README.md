# Wazuh SIEM Homelab — Detection Engineering Portfolio

A hands-on Wazuh SIEM lab built to practice detection engineering, custom rule writing, and MITRE ATT&CK mapping for SOC Analyst roles.

## Project Overview

This homelab simulates real-world attacks against a monitored Ubuntu target node and demonstrates how Wazuh detects them in real time. Each detection is mapped to the MITRE ATT&CK framework.

## Environment

| Component | Details |
|-----------|---------|
| Hypervisor | Proxmox VE 8.x (low-spec hardware) |
| Wazuh Server | Ubuntu Server 26.04, Wazuh 4.14.8 (All-in-One) |
| Target Node | Ubuntu Server 26.04 with Wazuh Agent 4.14.8 |
| Attacker | Kali Linux (Nmap, Hydra, Metasploit) |

## Completed Detections

| # | Attack | Rule ID | Level | MITRE Technique |
|---|--------|---------|-------|-----------------|
| 1 | Nmap Port Scan | 100101 | 8 | T1046 — Network Service Discovery |
| 2 | SSH Brute Force (in progress) | 100102 | 10 | T1110 — Brute Force |
| 3 | Backdoor User Creation (in progress) | 100103 | 12 | T1136 — Create Account |

## Detection 1 — Nmap Port Scan (T1046)

**Attack:** Ran an Nmap TCP connect scan from Kali against the target node.

**Detection:** Custom Wazuh rule correlates UFW block events from the same source IP within a 10-second window.

**Result:** Level 8 alert fired in real time, mapped to MITRE ATT&CK T1046.

**Rule file:** [`rules/local_rules.xml`](rules/local_rules.xml)

## What I'm Learning

- Custom Wazuh rule syntax and frequency-based correlation
- Log ingestion from UFW, auth.log, and file integrity monitoring
- MITRE ATT&CK framework mapping
- Building detection dashboards for SOC investigations

## Roadmap

- [x] Deploy Wazuh all-in-one stack
- [x] Enroll Linux agent
- [x] Detect Nmap port scan (T1046)
- [ ] Detect SSH brute force (T1110)
- [ ] Detect backdoor user creation (T1136)
- [ ] Add Suricata IDS integration
- [ ] Add Windows agent
- [ ] Build custom SOC dashboard

## Connect

Built by [Your Name] — [LinkedIn](https://linkedin.com/in/yourprofile)

Open to entry-level SOC Analyst opportunities in the UAE.
