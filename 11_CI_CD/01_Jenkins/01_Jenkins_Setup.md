# ⚙️ Jenkins Setup on AWS EC2

This section documents the setup of Jenkins on an AWS EC2 instance and initial configuration required to start building CI/CD pipelines.

---

## 📌 What is Jenkins?

Jenkins is an open-source automation server used to implement **Continuous Integration (CI)** and **Continuous Delivery (CD)** pipelines.

It automates:
- Code fetching from repositories
- Build processes
- Testing
- Deployment workflows

---

## 🧱 Infrastructure Details

| Component | Configuration |
|----------|-------------|
| Instance Type | t2.medium |
| OS | Ubuntu |
| Port | 8080 |
| Access | SSH (from my IP) |

---

## 🔐 Security Group Configuration

Inbound Rules:
- **SSH (22)** → My IP
- **Custom TCP (8080)** → My IP (Jenkins UI access)

---

## 🚀 Jenkins Installation Script

The following script was added in **EC2 Advanced User Data**:

```bash
#!/bin/bash

sudo apt update
sudo apt install fontconfig openjdk-21-jdk -y

java -version

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y
```

---

## 🔑 Initial Jenkins Setup

After launching the instance:

### Step 1: Access Jenkins UI
```
http://<EC2_PUBLIC_IP>:8080
```

### Step 2: Retrieve Admin Password
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### Step 3: Complete Setup
- Enter admin password
- Install suggested plugins
- Create admin user

---

## 🧠 Key Observations

- Jenkins runs as a service after installation
- Default port is `8080`
- Requires Java (JDK 21 used here)
- Initial setup requires unlocking using generated password

---

## ⚙️ Basic Job Creation (Exploration)

Created a simple **Freestyle Job** to understand execution:

### Sample Commands Used:

```bash
whoami
pwd
id
w
```

### File Creation Example:

```bash
cat /proc/cpuinfo > cpuinfo.txt
ls -ltr
pwd
```

---

## 📦 Artifact Archiving

Configured **Post-Build Action → Archive Artifacts**

```
**/*.txt
```

This stores generated files as build artifacts inside Jenkins.

---

## 🧪 Observations from Console Output

- Commands executed in Jenkins workspace
- Logs available in real-time
- Useful for debugging pipeline failures

---

## ⚠️ Issues Faced

### 🔸 Disk Space Error
```
No space left on device
```

### ✅ Fix
- Increased EBS volume from **8GB → 20GB**
- Rebooted instance

---

## 📊 Outcome

- Jenkins successfully installed and configured
- First job executed successfully
- Basic understanding of:
  - Job execution
  - Console logs
  - Artifact archiving

---

## 📌 Next Step

Move to:
- Freestyle vs Pipeline Jobs
- Pipeline as Code (Jenkinsfile)

---
