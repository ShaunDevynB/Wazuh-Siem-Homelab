# SSH Brute Force Simulation

## Objective
Simulate repeated failed SSH login attempts to trigger brute force detection.

## Command
```bash
for i in {1..15}; do ssh -o "StrictHostKeyChecking=no" baduser@localhost 2>/dev/null; sleep 1; done
```

## Wazuh Detection
- Rule 5710: sshd — Attempt to login using a non-existent user
- MITRE ATT&CK: T1110.001 (Brute Force: Password Guessing), T1021.004 (SSH)
- Tactic: Credential Access, Lateral Movement
- Severity: Level 5

## Result
15 authentication failures detected. Alerts visible in Security Events tab showing repeated login attempts from the same source with rule 5710 firing for each attempt.
