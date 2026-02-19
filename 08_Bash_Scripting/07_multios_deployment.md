# 07 - Multi-OS Deployment & Centralized Orchestration

This section documents cross-distribution deployment automation and centralized script orchestration across multiple servers.

Environment:
- scriptbox (control node)
- web01, web02, web03 (managed nodes)

Focus:
- OS detection logic
- yum vs apt branching
- Cross-platform provisioning
- Script distribution using scp
- Remote execution using ssh
- Centralized orchestration workflow

---

## 1. Multi-OS Deployment Script

### Script: `multios_websetup.sh`

This script detects the operating system and installs the appropriate web server packages.

### OS Detection Logic

```bash
yum --help &> /dev/null

if [ $? -eq 0 ]; then
   PACKAGE="httpd wget unzip"
   SVC="httpd"
else
   PACKAGE="apache2 wget unzip"
   SVC="apache2"
fi
```

If `yum` exists → assume CentOS/RHEL  
Else → assume Ubuntu/Debian

---

## 2. Cross-Distribution Deployment Flow

For both OS families:

1. Install required packages
2. Start and enable web service
3. Download website artifact
4. Extract archive
5. Copy files to `/var/www/html`
6. Restart service
7. Cleanup temporary files

Deployment Pattern:

```
Install → Start → Deploy → Restart → Cleanup
```

---

## 3. Centralized Deployment Script

### Script: `webdeploy.sh`

```bash
#!/bin/bash

USR='devops'

for host in $(cat remhosts)
do
   echo "#########################################"
   echo "Connecting to $host"
   echo "Pushing Script to $host"

   scp multios_websetup.sh $USR@$host:/tmp/

   echo "Executing Script on $host"
   ssh $USR@$host sudo /tmp/multios_websetup.sh

   ssh $USR@$host sudo rm -rf /tmp/multios_websetup.sh

   echo "#########################################"
done
```

---

## 4. Orchestration Flow

```
scriptbox
   │
   ├── remhosts (inventory)
   ├── scp → push script
   ├── ssh → execute with sudo
   └── ssh → cleanup
```

Each node:
- Receives deployment script
- Executes provisioning locally
- Cleans temporary files

---

## 5. Key Requirements

- SSH key-based authentication
- Passwordless sudo for devops user
- Network connectivity between nodes

---

## 6. DevOps Relevance

This implementation mirrors the architecture of configuration management systems.

Equivalent patterns in real tools:

| Tool | Equivalent Concept |
|------|-------------------|
| Ansible | Inventory + SSH + Task Execution |
| CI/CD | Deployment stage |
| Terraform + Provisioner | Remote-exec step |
| Kubernetes | Declarative service lifecycle |

This section demonstrates:

- Cross-platform automation
- Inventory-driven orchestration
- Centralized deployment control
- Agentless infrastructure management

---

## 7. Learning Outcomes

Through this implementation:

- Built a control-node architecture
- Implemented OS-aware branching logic
- Automated multi-node deployments
- Practiced script distribution and cleanup
- Simulated basic configuration management behavior

---

## Summary

Multi-OS deployment combined with centralized orchestration transforms simple Bash scripts into scalable infrastructure automation tools.

This represents foundational DevOps automation principles implemented manually before adopting advanced tooling.

