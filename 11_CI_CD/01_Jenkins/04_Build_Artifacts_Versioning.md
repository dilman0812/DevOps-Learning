# 📦 Build Artifacts & Versioning in Jenkins

This section covers how build artifacts are generated, stored, and versioned in Jenkins to ensure traceability and reproducibility.

---

## 📌 What are Build Artifacts?

Artifacts are the **output files generated after a successful build**, such as:

- `.war` files (Java web apps)
- `.jar` files
- Logs or reports

In this project:
```
target/vprofile-v2.war
```

---

## 🎯 Why Artifact Versioning is Important

- Track build history
- Enable rollback to previous versions
- Avoid overwriting builds
- Support reproducible deployments

---

## ⚙️ Basic Artifact Handling

After build:

```bash
mvn install -DskipTests
```

Artifacts generated in:
```
target/
```

---

## 📂 Archiving Artifacts in Jenkins

Configured using:

```
Post Build Action → Archive Artifacts
```

Pattern used:
```
**/target/*.war
```

---

## 🔢 Versioning Using BUILD_ID

Jenkins provides built-in environment variables.

### Example:

```bash
mkdir -p versions
cp target/vprofile-v2.war versions/vpro$BUILD_ID.war
```

### Output:
```
vpro1.war
vpro2.war
vpro3.war
```

---

## 🧪 Parameterized Builds

Enabled **Build with Parameters**:

- Parameter Name: `VERSION`

### Script:

```bash
mkdir -p versions
cp target/vprofile-v2.war versions/vpro$VERSION.war
```

### Example Run:
```
VERSION = 10 → vpro10.war
```

---

## ⏱️ Versioning Using Timestamp

Installed **Timestamp Plugin**.

### Script:

```bash
cp target/vprofile-v2.war versions/vpro$BUILD_TIMESTAMP.war
```

### Output:
```
vpro2026-04-25_16-45-12.war
```

---

## 📊 Versioning Strategies Used

| Strategy | Example | Use Case |
|---------|--------|--------|
| BUILD_ID | vpro12.war | Sequential builds |
| Parameter | vpro10.war | Manual control |
| Timestamp | vpro2026-04-25.war | Unique + traceable |

---

## ⚠️ Issues Faced

### 🔸 Disk Space Issue
```
No space left on device
```

### Cause:
- Multiple builds storing artifacts
- Default 8GB EBS volume insufficient

### ✅ Fix:
- Increased volume size to **20GB**
- Rebooted instance

---

## 🧠 Key Learnings

- Artifact versioning is critical in CI/CD pipelines
- Jenkins environment variables simplify version control
- Parameterized builds provide flexibility
- Storage planning is important in CI systems

---

## 📦 Transition to Artifact Repository

Local artifact storage is not scalable.

Next step:
- Store artifacts in **Nexus Repository**
- Centralized and version-controlled artifact management

---

## 📊 Outcome

- Implemented artifact archiving in Jenkins
- Applied multiple versioning strategies
- Prepared pipeline for integration with Nexus

---

## 📌 Next Step

- SonarQube Integration
- Code quality analysis in pipeline

---
