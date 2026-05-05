# 📦 Nexus Repository Integration with Jenkins

This section covers the integration of Nexus Repository Manager with Jenkins to store and manage build artifacts in a centralized and version-controlled manner.

---

## 📌 What is Nexus?

Nexus is an **artifact repository manager** used to store build outputs such as:

- `.war` files
- `.jar` files
- Docker images
- Dependencies

It acts as a **central storage system** for artifacts in CI/CD pipelines.

---

## 🎯 Why Use Nexus?

- Centralized artifact storage
- Version control for builds
- Supports rollback
- Enables sharing across environments
- Avoids dependency on Jenkins local storage

---

## 🧱 Infrastructure Setup

### 🔹 EC2 Instance
- OS: Amazon Linux
- Instance Type: t2.medium

### 🔹 Ports
- `8081` → Nexus UI

### 🔹 Security Groups
- SSH (22) → My IP
- Custom TCP (8081) → My IP
- Custom TCP (8081) → Jenkins Security Group

---

## ⚙️ Nexus Setup Summary

- Installed Java (Amazon Corretto 17)
- Downloaded Nexus package
- Configured systemd service
- Started and enabled Nexus service

---

## 🔐 Access Nexus

Open in browser:

```
http://<NEXUS_PUBLIC_IP>:8081
```

Login using admin credentials.

---

## 🗂️ Repository Creation

Created a repository:

- Type: `maven (hosted)`
- Name: `vprofile-repo`

Used for storing WAR artifacts.

---

## 🔑 Jenkins Integration

### Step 1: Add Credentials

```
Manage Jenkins → Credentials
```

Add:
- Username
- Password (Nexus login)

Example:
```
ID: nexuslogin
```

---

## 🔌 Required Plugin

Installed:
- Nexus Artifact Uploader Plugin

---

## 📜 Pipeline Integration

### Publish to Nexus Stage

```groovy
stage("Publish to Nexus") {
  steps {
    nexusArtifactUploader(
      nexusVersion: 'nexus3',
      protocol: 'http',
      nexusUrl: '<NEXUS_PRIVATE_IP>:8081',
      groupId: 'QA',
      version: "${env.BUILD_ID}-${BUILD_TIMESTAMP}",
      repository: 'vprofile-repo',
      credentialsId: 'nexuslogin',
      artifacts: [
        [
          artifactId: 'vproapp',
          classifier: '',
          file: 'target/vprofile-v2.war',
          type: 'war'
        ]
      ]
    )
  }
}
```

---

## 🔢 Artifact Versioning in Nexus

Artifacts stored with version:

```
BUILD_ID + BUILD_TIMESTAMP
```

Example:
```
vproapp-12-2026-04-25.war
```

---

## 🧪 Verification

Steps:
1. Ran Jenkins pipeline multiple times
2. Opened Nexus UI
3. Verified artifacts under:

```
vprofile-repo → QA → vproapp
```

Observed:
- Multiple versions stored
- No overwriting of artifacts

---

## ⚠️ Common Issues & Fixes

### 🔸 Connection Failure
- Ensure Nexus SG allows traffic from Jenkins SG

### 🔸 Authentication Error
- Verified Jenkins credentials

### 🔸 Wrong Artifact Path
- Correct path:
```
target/vprofile-v2.war
```

---

## 🧠 Key Learnings

- Nexus enables **centralized artifact management**
- Versioning ensures traceability
- Decouples build and deployment stages
- Critical for scalable CI/CD systems

---

## 📊 Outcome

- Successfully integrated Nexus with Jenkins
- Automated artifact upload in pipeline
- Verified versioned storage of builds

---

## 📌 Next Step

- Slack Notifications
- Real-time pipeline feedback system

---
