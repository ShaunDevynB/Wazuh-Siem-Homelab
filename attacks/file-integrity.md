# File Integrity Monitoring (FIM) Test

## Objective
Trigger Wazuh file integrity monitoring by modifying files in the /etc directory.

## Commands
```bash
sudo touch /etc/suspicious-file.txt
sudo echo "test" > /etc/suspicious-file.txt
sudo rm /etc/suspicious-file.txt
```

## Wazuh Detection
- Rules 550/553: Integrity checksum changed
- MITRE ATT&CK: T1565 (Data Manipulation)
- Tactic: Impact
- Severity: Level 7

## Result
Wazuh FIM module detected the file creation and modification events in /etc, a protected directory monitored by default.
