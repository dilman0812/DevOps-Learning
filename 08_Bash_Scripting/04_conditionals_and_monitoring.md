# 04 - Conditionals & Service Monitoring

This section documents decision-making logic, numeric comparisons, file tests, exit status handling, and service monitoring automation using Bash.

Focus:
- if / elif / else
- Numeric comparison operators
- Exit codes (`$?`)
- File tests (`-f`)
- Self-healing service monitoring
- Cron-based automation

---

## 1. Basic Conditional Example

### Script: Number Comparison

```bash
#!/bin/bash

read -p "Enter a number: " NUM

if [ "$NUM" -gt 100 ]; then
   echo "Your number is greater than 100"
else
   echo "Your number is less than or equal to 100"
fi

echo "Script execution completed successfully."
```

### Numeric Operators

| Operator | Meaning |
|----------|----------|
| -eq | equal |
| -ne | not equal |
| -gt | greater than |
| -lt | less than |
| -ge | greater or equal |
| -le | less or equal |

---

## 2. Exit Status Handling

Every command in Linux returns an exit code.

```bash
$?   # Holds exit status of previous command
```

- `0` → success
- Non-zero → failure

Example:

```bash
ls /var/run/httpd/httpd.pid &> /dev/null

if [ $? -eq 0 ]; then
   echo "File exists"
else
   echo "File not found"
fi
```

---

## 3. File Test Operators

Better approach than checking `$?`:

```bash
if [ -f /var/run/httpd/httpd.pid ]; then
   echo "File exists"
fi
```

Common file test flags:

| Flag | Meaning |
|------|----------|
| -f | Regular file exists |
| -d | Directory exists |
| -e | File exists (any type) |
| -x | File is executable |

---

## 4. Service Monitoring Script

### Script: `monitor_httpd.sh`

```bash
#!/bin/bash

echo "###################################################"
date

if systemctl is-active --quiet httpd; then
   echo "Httpd process is running."
else
   echo "Httpd process is NOT running."
   echo "Starting the process..."

   if systemctl start httpd; then
      echo "Process started successfully."
   else
      echo "Process starting failed. Contact the administrator."
   fi
fi

echo "###################################################"
```

---

## 5. Self-Healing Logic

Flow:

```
Check service → If down → Start service → Verify status
```

This mimics:
- Supervisor processes
- Systemd restart policies
- Kubernetes health checks
- Auto-healing infrastructure

---

## 6. Cron Integration

Script scheduled using:

```bash
crontab -e
```

Example cron entry:

```bash
*/5 * * * * /path/to/monitor_httpd.sh
```

Meaning:
- Runs every 5 minutes
- Checks service health
- Restarts if down

---

## 7. DevOps Relevance

This section demonstrates:

- Decision-making automation
- Health check scripting
- Self-recovery logic
- Scheduled monitoring
- Operational resilience patterns

Conditionals form the foundation for:

- Deployment branching
- Error handling
- Failover logic
- Infrastructure validation
- CI/CD pipeline checks

---

## Summary

Conditionals and monitoring scripts introduce operational control logic into automation workflows.

They transform static scripts into intelligent, self-aware automation tools.

