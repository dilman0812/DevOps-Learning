# 08 - Bash Scripting (DevOps-Oriented Automation)

This directory documents hands-on Bash scripting concepts implemented as part of foundational DevOps training.

All scripts were developed and tested in a multi-VM environment:

- scriptbox (Control Node)
- web01
- web02
- web03

The focus was not just learning syntax, but applying Bash to real infrastructure automation problems.

---

## 📚 Topics Covered

### 1. Bash Fundamentals
- Shebang usage
- Variables & exporting
- Command substitution
- Quoting rules
- Positional parameters
- Exit codes
- File test operators

---

### 2. System Information Automation
- Memory parsing (`free`)
- Load average extraction (`uptime`)
- Disk usage checks (`df`)
- Text processing with `awk`

Built system monitoring scripts for health inspection.

---

### 3. Static Web Deployment Automation
- Package installation (yum / apt)
- Service management (systemctl)
- Artifact download & extraction
- Deployment to `/var/www/html`
- Service restart & cleanup

Simulated a simplified CI/CD deployment workflow.

---

### 4. Conditionals & Monitoring
- if / elif / else
- Numeric comparisons
- Exit status handling (`$?`)
- Service health checks
- Self-healing automation logic
- Cron-based scheduled monitoring

Implemented basic auto-recovery behavior for httpd.

---

### 5. Loops & Iteration
- for loops (list-based)
- while loops (condition-based)
- Arithmetic expansion
- Bulk user provisioning
- Multi-service execution patterns

Enabled scalable automation across multiple resources.

---

### 6. Remote Command Execution
- SSH basics
- Key-based authentication
- Passwordless sudo configuration
- Inventory-driven remote execution
- Multi-node command orchestration

Implemented agentless remote execution similar to Ansible architecture.

---

### 7. Multi-OS Deployment Logic
- OS detection (yum vs apt)
- Cross-distribution package handling
- Centralized script distribution using scp
- Remote execution using ssh
- Cleanup after execution

Built a centralized deployment orchestrator capable of provisioning multiple nodes.

---

## 🏗 Architecture Implemented

```
scriptbox (control node)
   │
   ├── remhosts (inventory file)
   ├── multios_websetup.sh (provision script)
   └── webdeploy.sh (orchestrator)
         │
         ├── scp → push script
         ├── ssh → execute with sudo
         └── cleanup
```

This simulates basic configuration management and deployment pipelines.

---

## 🎯 Learning Objectives Achieved

- Transitioned from basic scripting to infrastructure automation
- Implemented environment-aware provisioning
- Automated multi-node deployments
- Practiced self-healing service monitoring
- Understood SSH-based orchestration models
- Built foundational skills before adopting higher-level tools like Ansible

---

## 🔍 Key Takeaway

Bash scripting is not just about syntax.

It is about:
- Automating repeatable tasks
- Managing infrastructure programmatically
- Designing resilient workflows
- Understanding what configuration management tools do under the hood

This section establishes strong DevOps automation fundamentals.

