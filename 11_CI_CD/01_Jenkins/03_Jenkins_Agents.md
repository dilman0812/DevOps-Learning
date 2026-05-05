# 🖥️ Jenkins Agents (Distributed Builds)

This section covers the setup and usage of **Jenkins Agents** to enable distributed builds and improve scalability of CI/CD pipelines.

---

## 📌 What are Jenkins Agents?

Jenkins Agents (also called **nodes or workers**) are machines that execute build jobs on behalf of the Jenkins controller.

### 🔹 Why Agents are Needed
- Offload build workload from controller
- Enable parallel builds
- Support different environments (Java, Node, Docker, etc.)
- Improve scalability

---

## 🧱 Architecture

```
Jenkins Controller (Master)
        |
        |  SSH Connection
        ↓
Jenkins Agent (Worker Node)
```

---

## 🚀 Agent Setup (AWS EC2)

### 🔹 Step 1: Launch EC2 Instance
- OS: Ubuntu
- Instance: t2.medium
- Security Group:
  - SSH (22) → Allow from Jenkins SG

---

## ⚙️ Step 2: Install Java on Agent

SSH into agent and run:

```bash
sudo -i
apt update
apt install openjdk-21-jdk -y
java -version
```

---

## 📁 Step 3: Prepare Workspace Directory

```bash
mkdir /opt/jenkins
chown ubuntu:ubuntu /opt/jenkins
```

Verify:

```bash
ls -ld /opt/jenkins
```

---

## 🔐 Step 4: Configure Agent in Jenkins

Go to:

```
Manage Jenkins → Nodes → New Node
```

### Configuration:
- Node Name: `MavenBuilder`
- Type: Permanent Agent
- Remote Root Directory: `/opt/jenkins`
- Labels: `MAVENBUILDER`
- Launch Method: **Launch via SSH**
- Host: `<Agent Private IP>`
- Credentials: SSH key

---

## ✅ Connection Status

After configuration:

- Agent status: **Online**
- Logs confirm successful connection

---

## 🔄 Running Jobs on Agent

To run a job on the agent:

### Step:
- Open Job → Configure
- Enable:
```
Restrict where this project can be run
```
- Enter label:
```
MAVENBUILDER
```

---

## 🧪 Observed Output

From console logs:

```
Building remotely on MavenBuilder (MAVENBUILDER)
in workspace /opt/jenkins/workspace/FirstJob
```

---

## 📦 Use Case in Project

- Used agent for:
  - Maven builds
  - Dependency downloads
  - Faster execution

---

## ⚠️ Common Issues & Fixes

### 🔸 Permission Issues
Fix:
```bash
chown ubuntu:ubuntu /opt/jenkins
```

### 🔸 SSH Connection Failure
- Check Security Group rules
- Verify key pair and credentials

---

## 🧠 Key Learnings

- Jenkins controller should not handle heavy workloads
- Agents enable horizontal scaling
- Labels allow workload targeting

---

## 📊 Outcome

- Successfully configured Jenkins agent on EC2
- Executed jobs remotely
- Implemented distributed build architecture

---

## 📌 Next Step

- Build artifact versioning
- Parameterized builds
- Managing build outputs

---
