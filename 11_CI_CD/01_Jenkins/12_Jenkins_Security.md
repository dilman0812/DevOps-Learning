# 🔐 Jenkins Security (Authentication & Authorization)

This section covers the basics of securing Jenkins by managing users, permissions, and access control.

---

## 📌 Why Jenkins Security is Important

Jenkins is a critical component in CI/CD pipelines. Without proper security:

- Unauthorized users can trigger builds
- Sensitive credentials can be exposed
- Pipelines can be modified maliciously
- Production systems can be impacted

---

## 🔑 Key Security Concepts

### 🔹 Authentication
Verifies **who the user is**

### 🔹 Authorization
Determines **what the user is allowed to do**

---

## 👤 User Management

### Step:

```
Manage Jenkins → Manage Users
```

- Created users
- Managed access levels
- Assigned credentials

---

## 🔐 Authentication Setup

Jenkins supports multiple authentication methods:

- Jenkins own user database (used here)
- LDAP
- OAuth (GitHub, Google)

---

## 🛂 Authorization (Access Control)

Configured using:

```
Manage Jenkins → Configure Global Security
```

---

## 🔹 Role-Based Strategy

Used **Role-Based Authorization Strategy Plugin**

### Types of Roles:

| Role Type | Purpose |
|----------|--------|
| Global Roles | Overall Jenkins access |
| Project Roles | Job-level permissions |
| Agent Roles | Node-level access |

---

## ⚙️ Example Role Setup

### 🔸 Admin Role
- Full access to:
  - Jobs
  - Nodes
  - Configuration
  - Plugins

### 🔸 Developer Role
- Permissions:
  - Build jobs
  - View logs
  - Read access

---

## 🔑 Credentials Management

Stored securely in:

```
Manage Jenkins → Credentials
```

Used for:
- GitHub access
- Nexus login
- AWS credentials
- SonarQube tokens

---

## ⚠️ Best Practices

- Do not hardcode credentials in Jenkinsfile
- Use credential IDs instead
- Limit access using least privilege principle
- Regularly rotate credentials

---

## 🧪 Observations

- Role-based access helps isolate permissions
- Credentials store integrates with pipelines
- Security configuration affects pipeline execution

---

## 🧠 Key Learnings

- Authentication and authorization are critical for CI/CD security
- Role-based access improves control and safety
- Secure credential management prevents leaks

---

## 📊 Outcome

- Configured Jenkins security with users and roles
- Implemented access control strategies
- Secured credentials for pipeline integrations

---

## 🎯 Final Outcome of Jenkins Module

Successfully implemented a **complete CI/CD system** with:

- Jenkins (CI/CD orchestration)
- SonarQube (code quality)
- Nexus (artifact repository)
- Docker + ECR (containerization)
- ECS (deployment)
- Slack (notifications)
- Job triggers (automation)
- Security (user & access control)

---

## 📌 Next Step

- GitHub Actions CI/CD
- GitLab CI/CD

---
