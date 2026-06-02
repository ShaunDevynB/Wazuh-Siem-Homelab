# Rogue Root User Creation

## Objective
Create a user with UID 0 (same privileges as root) to simulate persistence technique.

## Commands
```bash
sudo useradd -o -u 0 -g 0 -M eviluser
sudo userdel eviluser
```

## Wazuh Detection
- Rule 5902: New user added to the system
- MITRE ATT&CK: T1136 (Create Account)
- Tactic: Persistence
- Severity: Level 8

## Result
Wazuh immediately fired rule 5902 at severity level 8 (higher than other alerts) detecting the new account creation. The warning "eviluser's uid 0 outside of the UID_MIN 1000 and UID_MAX 60000 range" confirms the rogue root-level account was created and detected.
