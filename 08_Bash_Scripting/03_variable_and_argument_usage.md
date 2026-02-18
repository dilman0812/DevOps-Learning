# 03 - Variables, Arguments & Environment Handling

This section documents the use of variables, positional parameters, quoting rules, exporting variables, and environment configuration in Bash scripting.

Focus:
- Variable declaration
- Positional parameters
- Argument validation
- Quoting rules
- Command substitution
- Exported variables
- Shell initialization files

---

## 1. Variable Declaration

Example:

```bash
PACKAGE="httpd wget unzip"
SVC="httpd"
URL="https://www.tooplate.com/zip-templates/2098_health.zip"
ART_NAME="2098_health"
TEMPDIR="/tmp/webfiles"
```

Benefits:
- Centralized configuration
- Easier maintenance
- Reusability
- Reduced hardcoding

---

## 2. Positional Parameters

Using runtime arguments:

```bash
wget "$1"
unzip "$2.zip"
sudo cp -r "$2"/* /var/www/html/
```

Execution:

```bash
./deploy.sh <URL> <ARTIFACT_NAME>
```

Where:
- `$1` → URL
- `$2` → extracted folder name

---

## 3. Argument Validation

```bash
if [ $# -ne 2 ]; then
  echo "Usage: $0 <URL> <ARTIFACT_FOLDER_NAME>"
  exit 1
fi
```

Special variables:
- `$#` → number of arguments
- `$0` → script name
- `$1`, `$2` → positional parameters

---

## 4. Quoting Rules

### Double Quotes `" "`
- Variables expand
- Command substitution works
- Safe for spaces

Example:

```bash
echo "User is $USER"
```

---

### Single Quotes `' '`
- No variable expansion
- Literal interpretation

Example:

```bash
echo 'User is $USER'
```

---

### Best Practice

Always quote variables:

```bash
cd "$TEMPDIR" || exit
wget "$URL"
```

Prevents:
- Word splitting issues
- Unexpected glob expansion
- Script failures due to spaces

---

## 5. Command Substitution

Modern form:

```bash
VAR=$(command)
```

Legacy form:

```bash
VAR=`command`
```

Preferred: `$( )`

Example:

```bash
FREERAM=$(free -m | awk '/Mem:/ {print $4}')
```

---

## 6. Exporting Variables

Normal variable:

```bash
NAME="devops"
```

Exported variable:

```bash
export NAME="devops"
```

Exported variables:
- Are available to child processes
- Become environment variables

---

### Testing Export

```bash
export TEST="hello"
env | grep TEST
```

---

## 7. Shell Initialization Files

### `~/.bashrc`
- User-specific
- Loaded in interactive shells

### `/etc/profile`
- System-wide
- Loaded for login shells

Environment variables added here persist across sessions.

---

## 8. DevOps Relevance

These concepts enable:

- Runtime configuration
- Parameterized deployments
- CI/CD variable injection
- Secret handling via environment variables
- Cross-environment scripting
- Safe and predictable automation

---

## Summary

This section establishes structured and reusable scripting practices through:

- Variable abstraction
- Argument-driven execution
- Safe quoting
- Environment-level configuration

