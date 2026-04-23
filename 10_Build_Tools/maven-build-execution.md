# ⚙️ Maven Build Execution — EC2 & CloudShell

This document captures hands-on build execution using Apache Maven across different cloud environments, focusing on reproducibility, version control, and artifact generation.

---

## 📌 Objective

- Execute Maven-based Java build in cloud environments  
- Validate build lifecycle and artifact generation  
- Ensure consistency across different OS setups  
- Understand impact of JDK and Maven versions  

---

## 🌐 Environment 1 — EC2 (Ubuntu)

### Setup

```bash
# Connect to instance
ssh -i key.pem ubuntu@<public-ip>

# Clone repository
git clone <your-repo-url>
cd vprofile-project
```

---

### JDK Installation & Switching

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
sudo apt install openjdk-21-jdk -y

# Switch versions
sudo update-alternatives --config java
```

---

### Maven Installation (Manual - Version Controlled)

```bash
wget https://archive.apache.org/dist/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.tar.gz

tar -xvzf apache-maven-3.9.9-bin.tar.gz
sudo mv apache-maven-3.9.9 /usr/local/maven3.9
```

---

### Build Execution

```bash
/usr/local/maven3.9/bin/mvn clean install
```

---

### Observations

- `target/` directory generated  
- Artifact (`.jar/.war`) created  
- Dependencies downloaded to:
  ```
  ~/.m2/repository
  ```

---

## ☁️ Environment 2 — AWS CloudShell (Amazon Linux)

### Setup

```bash
# Install JDK (Amazon Corretto)
sudo dnf install java-21-amazon-corretto -y

# Install Maven
sudo dnf install maven -y
```

---

### Clone & Build

```bash
git clone <your-repo-url>
cd vprofile-project

mvn clean install
```

---

### Observations

- Faster setup due to pre-configured environment  
- No manual binary management required  
- Same `target/` artifact generated  
- Confirms build reproducibility across environments  

---

## 🌐 Additional Build — Node.js Microservice

### Setup & Build

```bash
# Install Node.js (if not present)
sudo dnf install nodejs -y   # (CloudShell)

# Install dependencies
npm install

# Run / build service
npm start
```

---

### Observations

- Uses `package.json` instead of `pom.xml`  
- Dependency management via `npm`  
- No strict lifecycle like Maven  
- Faster but less standardized compared to Java builds  

---

## 📊 Key Comparisons

| Aspect            | EC2 Ubuntu                  | AWS CloudShell              |
|------------------|----------------------------|-----------------------------|
| Setup Time        | Higher (manual install)    | Low (managed environment)   |
| Control           | Full control               | Limited control             |
| Maven Version     | Custom (3.9.x)             | Package-managed             |
| Reproducibility   | High (version pinned)      | Moderate                    |

---

## 📌 Key Takeaways

- Build execution must be environment-independent  
- Manual installation enables strict version control  
- Managed environments optimize speed but reduce control  
- Artifact generation (`target/`) is consistent across setups  
- Multi-language builds require different tooling approaches  

---

## 🚀 Outcome

- Successfully executed Maven builds in multiple environments  
- Generated deployable artifacts  
- Validated cross-environment consistency  
- Established foundation for CI/CD integration  
