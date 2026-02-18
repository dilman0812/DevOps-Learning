# 01 - Bash Basics & System Information Automation

This section covers foundational Bash scripting concepts implemented in a Linux VM environment as part of DevOps fundamentals.

Focus:
- Shebang usage
- Echo & formatting
- Environment variables
- Command substitution
- Basic system monitoring commands
- Text parsing using `awk`

---

## 1. Shebang

```bash
#!/bin/bash
```

Defines the interpreter for the script.  
Ensures the script runs using Bash instead of the system’s default shell.

---

## 2. Basic System Info Script

### Script: `system_info.sh`

```bash
#!/bin/bash

echo "Welcome $USER on $HOSTNAME."
echo "#########################################"

FREERAM=$(free -m | awk '/Mem:/ {print $4}')
LOAD=$(uptime | awk -F'load average:' '{print $2}')
ROOTFREE=$(df -h / | awk 'NR==2 {print $4}')

echo "#########################################"
echo "Available free RAM is $FREERAM MB"
echo "#########################################"
echo "Current Load Average:$LOAD"
echo "#########################################"
echo "Free ROOT partition size is $ROOTFREE"
```

---

## 3. Concepts Implemented

### Environment Variables
- `$USER`
- `$HOSTNAME`

These are inherited from the shell environment.

---

### Command Substitution

```bash
VAR=$(command)
```

Used to store command output inside variables.

Example:

```bash
FREERAM=$(free -m | awk '/Mem:/ {print $4}')
```

---

### Pipelines

```bash
command1 | command2 | command3
```

Used to filter and process output.

Example:

```bash
free -m | awk '/Mem:/ {print $4}'
```

---

### Text Processing with `awk`

Used for column extraction and pattern filtering.

Examples:

```bash
awk '/Mem:/ {print $4}'
awk -F'load average:' '{print $2}'
```

---

## 4. Key Linux Commands Used

| Command | Purpose |
|----------|----------|
| `free -m` | Displays memory usage in MB |
| `uptime` | Shows load average |
| `df -h` | Displays disk usage |
| `awk` | Field extraction |
| `echo` | Output formatting |

---

## 5. DevOps Relevance

This script demonstrates:

- Basic system health inspection
- Output parsing
- Automation of manual monitoring checks
- Structured script formatting

This forms the foundation for:
- Monitoring scripts
- Health checks
- CI/CD environment validation
- Infrastructure diagnostics

---

## 6. Execution

```bash
chmod +x system_info.sh
./system_info.sh
```

---

## Summary

This section establishes core Bash scripting foundations required for:

- Deployment automation
- Monitoring scripts
- Infrastructure provisioning
- Remote execution workflows

