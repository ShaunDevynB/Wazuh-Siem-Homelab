# Wazuh SIEM Home Lab

## Overview
Deployed a cloud-based SIEM home lab using Wazuh on AWS EC2 with two Ubuntu instances. One instance runs the Wazuh Manager, Indexer, and Dashboard. The second acts as a monitored endpoint running the Wazuh Agent. Simulated real attack scenarios and analyzed the resulting alerts mapped to the MITRE ATT&CK framework.

## Architecture
Mac (Local)
└── SSH via .pem key
├── AWS EC2 — ManagerShaun (c7i.flex.large, Ubuntu 24.04)
│   └── Wazuh Manager + Indexer + Dashboard
└── AWS EC2 — ShaunAgent (t3.micro, Ubuntu 26.04)
└── Wazuh Agent 
## Tools Used
- Wazuh 4.7.5 (SIEM / XDR)
- AWS EC2 (cloud infrastructure)
- Ubuntu Server 24.04 LTS
- SSH key-based authentication (.pem)

## Attack Simulations

| Technique | MITRE ATT&CK | Wazuh Rule | Tactic |
|---|---|---|---|
| SSH brute force | T1110.001, T1021.004 | 5710 | Credential Access, Lateral Movement |
| Rogue root user created | T1136 | 5902 | Persistence |
| Privilege escalation (SUID) | T1548.003 | 5402 | Privilege Escalation, Defense Evasion |
| Sudo to ROOT executed | T1548.003 | 5402 | Privilege Escalation, Defense Evasion |
| PAM session monitoring | T1078 | 5501 | Defense Evasion, Persistence, Initial Access |

## Results
- 122 total alerts generated during attack simulations
- 15 authentication failures detected
- 7 distinct MITRE ATT&CK techniques mapped
- Alerts categorized across 6 tactics: Credential Access, Lateral Movement, Persistence, Privilege Escalation, Defense Evasion, Initial Access

## Screenshots
See `/screenshots` folder for full dashboard evidence.

## What I Learned
- How to deploy and configure a SIEM in a cloud environment using AWS EC2
- How Wazuh agents communicate with the central manager to forward logs and events
- How to simulate real attack techniques and observe how a SIEM detects and categorizes them
- How Wazuh maps alerts to the MITRE ATT&CK framework automatically
- Alert triage — reading rule IDs, severity levels, and tactics to understand what happened on an endpoint

## Resume Bullet
> Deployed a cloud-based Wazuh SIEM lab on AWS EC2; configured manager-agent architecture, simulated 5 attack techniques (brute force, privilege escalation, persistence, lateral movement), and analyzed 122 resulting alerts mapped to MITRE ATT&CK framework.
