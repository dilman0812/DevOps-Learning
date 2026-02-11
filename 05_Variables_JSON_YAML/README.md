# Variables, JSON & YAML in DevOps

This module covers configuration fundamentals used extensively across DevOps workflows, automation tooling, and cloud-native systems.

Understanding variables and structured data formats is critical for working with Docker, Kubernetes, CI/CD pipelines, Infrastructure as Code, and cloud services.

---

# 1️⃣ Environment Variables (Linux)

Environment variables are dynamic key-value pairs used by the operating system and applications to configure runtime behavior.

## Setting Variables

### Temporary (current session only)

```bash
export APP_ENV=production
echo $APP_ENV
```

### Permanent (user-level)

Add to `~/.bashrc`:

```bash
export APP_ENV=production
```

Reload:

```bash
source ~/.bashrc
```

### System-wide

Edit:

```bash
/etc/environment
```

---

## Scope of Variables

| Type        | Scope         | Lifetime            |
|-------------|--------------|--------------------|
| Local       | Current shell | Until session ends |
| User-level  | Specific user | Persistent         |
| System-wide | All users     | Persistent         |

---

## Example Use Case

Applications read environment variables for:

- Database credentials
- API keys
- Application modes (dev/staging/prod)
- Port configuration

Example in Bash:

```bash
#!/bin/bash
echo "Application running in $APP_ENV mode"
```

(See `examples/env_demo.sh`)

---

# 2️⃣ JSON (JavaScript Object Notation)

JSON is a lightweight data-interchange format widely used in APIs, configuration files, and cloud services.

## Structure

- Key-value pairs
- Supports nested objects
- Uses `{}` for objects and `[]` for arrays

Example:

```json
{
  "app": "vprofile",
  "version": "1.0",
  "database": {
    "host": "localhost",
    "port": 3306
  }
}
```

(See `examples/sample.json`)

---

## Parsing JSON in Linux

Using `jq`:

```bash
cat sample.json | jq '.database.host'
```

Common use cases:

- CI/CD pipelines
- API responses
- Terraform outputs
- Cloud service responses

---

# 3️⃣ YAML (YAML Ain't Markup Language)

YAML is a human-readable configuration format heavily used in DevOps tools.

Used in:

- Docker Compose
- Kubernetes manifests
- GitHub Actions
- Ansible playbooks

---

## YAML Rules

- Indentation matters (spaces only, no tabs)
- Key-value format
- Lists use `-`
- Supports comments using `#`

Example:

```yaml
app:
  name: vprofile
  version: "1.0"
  database:
    host: localhost
    port: 3306
```

(See `examples/sample.yaml`)

---

## YAML vs JSON

| Feature              | JSON | YAML |
|----------------------|------|------|
| Readability          | Moderate | High |
| Comments             | ❌ Not allowed | ✅ Allowed |
| Used in APIs         | Yes | Rare |
| Used in DevOps configs | Limited | Very common |

---

# DevOps Relevance

These configuration formats are foundational for:

- Container configuration
- Infrastructure as Code
- CI/CD pipeline definitions
- Service communication
- Cloud resource provisioning

Mastering them ensures consistent and reproducible system configuration across environments.

---

# Key Takeaways

- Environment variables externalize configuration from code.
- JSON is dominant in APIs and structured data exchange.
- YAML is the primary configuration format in modern DevOps tooling.
- Configuration discipline directly impacts system reliability and automation maturity.

