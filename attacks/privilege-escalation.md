# Privilege Escalation Simulation

## Objective
Simulate privilege escalation by setting the SUID bit and executing sudo to ROOT.

## Commands
```bash
touch /tmp/testbinary
sudo chmod u+s /tmp/testbinary
```

## Wazuh Detection
- Rule 5402: Successful sudo to ROOT executed
- MITRE ATT&CK: T1548.003 (Abuse Elevation Control Mechanism: Sudo and Sudo Caching)
- Tactic: Privilege Escalation, Defense Evasion
- Severity: Level 3

## Result
Wazuh detected the sudo ROOT execution and SUID bit change, firing rule 5402 mapped to MITRE T1548.003.
