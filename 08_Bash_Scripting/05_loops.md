# 05 - Loops & Iterative Automation

This section documents iterative control structures in Bash using `for` and `while` loops.

Focus:
- for loops (list-based)
- for loops with variables
- while loops (condition-based)
- Arithmetic expansion
- Bulk user management
- Iterative automation patterns

---

## 1. Basic For Loop

### Example

```bash
#!/bin/bash

for VAR1 in java .net python ruby php
do
  echo "Looping..."
  sleep 1
  echo "########################################"
  echo "Value of VAR1 is $VAR1"
  echo "########################################"
  date
  echo
done
```

Execution Flow:

```
java → .net → python → ruby → php
```

Each value is assigned to `VAR1` sequentially.

---

## 2. For Loop Using Variable List

### Example: User Creation Script

```bash
#!/bin/bash

MYUSERS="alpha beta gamma"

for usr in $MYUSERS
do
   echo "Adding user $usr."
   useradd "$usr"
   id "$usr"
   echo "############################"
done
```

### Concept

- Iterates over space-separated values
- Automates bulk operations
- Executes same command for multiple inputs

---

### Idempotent Improvement

```bash
if id "$usr" &>/dev/null; then
   echo "User $usr already exists."
else
   useradd "$usr"
   echo "User $usr created."
fi
```

Prevents script failure on re-run.

---

## 3. While Loop (Condition-Based)

### Example

```bash
#!/bin/bash

counter=0

while [ "$counter" -lt 5 ]
do
  echo "Looping..."
  echo "Value of counter is $counter."
  counter=$((counter + 1))
  sleep 1
done

echo "Out of the loop"
```

Execution Flow:

```
0 → 1 → 2 → 3 → 4
```

Loop exits when condition becomes false.

---

## 4. Arithmetic Expansion

```bash
counter=$((counter + 1))
```

Alternative:

```bash
((counter++))
```

Used for numeric iteration.

---

## 5. For vs While

| for Loop | while Loop |
|-----------|------------|
| Iterates over list | Runs based on condition |
| Used for fixed items | Used for dynamic checks |
| Cleaner for known values | Better for polling & retries |

---

## 6. DevOps Relevance

Loops enable:

- Bulk user creation
- Multi-server operations
- Restarting multiple services
- Deploying across environments
- Iterative monitoring
- Retry logic
- Infrastructure scaling

Example real-world pattern:

```bash
SERVICES="nginx mysql redis"

for svc in $SERVICES
do
   systemctl restart "$svc"
done
```

---

## Summary

Loops transform scripts from single-execution utilities into scalable automation tools capable of handling multiple resources efficiently.

They are foundational for infrastructure orchestration and bulk operations.

