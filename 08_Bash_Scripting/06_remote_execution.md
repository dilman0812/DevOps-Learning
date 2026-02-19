# 06 - Remote Command Execution & SSH Automation

This section documents remote command execution using SSH, key-based authentication, inventory-driven loops, and non-interactive automation across multiple servers.

Environment Used:
- scriptbox (control node)
- web01
- web02
- web03

Focus:
- SSH basics
- Key-based authentication
- Passwordless automation
- Inventory file usage
- Remote command execution loops

---

## 1. Basic Remote Command Execution

From the control node (scriptbox):

```bash
ssh web01 "uptime"
ssh web02 "uptime"
ssh web03 "uptime"
```

Flow:

```
scriptbox → SSH → remote node → execute command → return output
```

The command runs on the remote server, not locally.

---

## 2. SSH Key-Based Authentication

To enable non-interactive automation:

```bash
ssh-keygen
ssh-copy-id devops@web01
ssh-copy-id devops@web02
ssh-copy-id devops@web03
```

This allows:
- Passwordless login
- Scriptable remote execution
- Automation-ready infrastructure

---

## 3. Inventory File

Created an inventory file named `remhosts`:

```
web01
web02
web03
```

Used for iterating across hosts.

---

## 4. Loop-Based Remote Execution

```bash
for host in $(cat remhosts)
do
   ssh devops@$host uptime
done
```

Improved version:

```bash
while read -r host
do
   ssh "devops@$host" uptime
done < remhosts
```

Benefits:
- Scalable
- Cleaner structure
- Inventory-driven automation

---

## 5. Passwordless Sudo Requirement

Remote script execution required:

```
devops ALL=(ALL) NOPASSWD: ALL
```

Configured in sudoers file.

This enables:

```bash
ssh devops@web01 sudo systemctl restart httpd
```

Without password prompt.

---

## 6. DevOps Relevance

This setup mirrors real-world configuration management systems.

Equivalent patterns:

- Ansible (agentless SSH model)
- CI/CD deployment jobs
- Infrastructure orchestration scripts
- Cluster-wide operations

Remote execution enables:

- Service restarts across nodes
- Log collection
- Patch updates
- Deployment automation
- Multi-node monitoring

---

## 7. Architecture Overview

```
scriptbox (control node)
   │
   ├── SSH key authentication
   │
   ├── Inventory file (remhosts)
   │
   └── Loop execution → web01 / web02 / web03
```

This forms the foundation for scalable infrastructure automation.

---

## Summary

Remote command execution combined with SSH key-based authentication transforms local Bash scripts into distributed infrastructure management tools.

This is the foundation for configuration management and deployment orchestration.

