# Wazuh Manager Installation

## Environment
- Cloud: AWS EC2
- Instance type: c7i.flex.large
- OS: Ubuntu 24.04 LTS (x86_64)
- Region: us-east-2 (Ohio)

## Steps

### 1. Launch EC2 instance
- AMI: Ubuntu Server 24.04 LTS
- Instance type: c7i.flex.large (2 vCPU, 4GB RAM)
- Key pair: wazuh-key.pem
- Security group inbound rules:
  - Port 22 (SSH) — My IP only
  - Port 443 (HTTPS) — My IP only
  - Port 1514 (Wazuh agent) — Anywhere
  - Port 1515 (Wazuh enrollment) — Anywhere
- Storage: 50 GiB gp3

### 2. SSH into the instance
```bash
chmod 400 ~/.ssh/wazuh-key.pem
ssh -i ~/.ssh/wazuh-key.pem ubuntu@PUBLIC_IP
```

### 3. Update the system
```bash
sudo apt-get update && sudo apt-get upgrade -y
```

### 4. Download and run the Wazuh installer
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a --ignore-check
```

### 5. Verify services
```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

### 6. Access dashboard
Navigate to `https://PUBLIC_IP` in browser.
Login with credentials printed at end of installer output.
