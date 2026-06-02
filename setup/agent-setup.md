# Wazuh Agent Installation

## Environment
- Cloud: AWS EC2
- Instance type: t3.micro
- OS: Ubuntu 26.04 LTS (x86_64)
- Region: us-east-2 (Ohio)

## Steps

### 1. Launch EC2 instance
- Same key pair as manager (wazuh-key.pem)
- Security group: allow SSH port 22 from My IP

### 2. SSH into agent instance
```bash
ssh -i ~/.ssh/wazuh-key.pem ubuntu@AGENT_PUBLIC_IP
```

### 3. Install the Wazuh agent
```bash
curl -so wazuh-agent.deb \
  https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.7.5-1_amd64.deb

sudo WAZUH_MANAGER='MANAGER_PUBLIC_IP' \
  WAZUH_AGENT_NAME='aws-agent' \
  dpkg -i ./wazuh-agent.deb
```

### 4. Start the agent
```bash
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

### 5. Verify connection
Agent appears as Active in Wazuh dashboard under Agents within 1-2 minutes.
