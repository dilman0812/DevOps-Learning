# 🔧 10_Build_Tools — Maven & Build Automation

This module documents the fundamentals of build systems and hands-on implementation using Maven in cloud environments.

---

## 📌 What is a Build Process?

The build process transforms source code into a deployable artifact.

**Stages:**
- Source Code → Developer-written application code
- Compile → Converts code into executable format
- Test → Validates correctness using unit/integration tests
- Package → Bundles code into `.jar` / `.war`
- Install/Deploy → Makes artifact available for execution or distribution

---

## 📌 Build Tools

Build tools automate and standardize the build lifecycle.

**Examples:**
- Java → Apache Maven, Gradle, Ant  
- .NET → MSBuild, NAnt  
- C/C++ → Make  

---

## ☕ Focus: Apache Maven

Apache Maven is a build automation tool primarily used for Java projects.

**Key Capabilities:**
- Dependency management
- Standardized lifecycle
- Plugin-based architecture
- Reproducible builds

---

## 📌 Maven Lifecycle

```
validate → compile → test → package → integration-test → verify → install → deploy
```

---

## ⚙️ Hands-on Environments

This module demonstrates builds across two environments:

### 1️⃣ EC2 Ubuntu Instance
- Manual JDK installation (17 & 21)
- Manual Maven installation (3.9.x)
- Version switching using `update-alternatives`
- Build execution using custom Maven binary

### 2️⃣ AWS CloudShell (Amazon Linux)
- Installed Corretto JDK 21
- Installed Maven via package manager
- Faster setup with managed environment

---

## 📦 Output

- `target/` directory generated after build
- Contains compiled artifact (`.jar/.war`)
- Dependencies stored in:
  ```
  ~/.m2/repository
  ```

---

## 🌐 Additional Build (Node.js)

A Node.js-based microservice was also built to understand:
- Multi-language build workflows
- Package managers (`npm`)
- Differences from Java build lifecycle

---

## 📌 Key Learnings

- Build systems must be reproducible across environments
- Tool/version consistency is critical
- Maven simplifies dependency and lifecycle management
- Cloud environments reduce setup complexity
- Build artifacts are primary inputs for CI/CD pipelines

---

## 🚀 Next Steps

- Deep dive into `pom.xml`
- Maven plugins (compiler, surefire)
- CI/CD integration (Jenkins / GitHub Actions)
