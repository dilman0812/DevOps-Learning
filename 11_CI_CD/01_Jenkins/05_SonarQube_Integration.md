# 🔍 SonarQube Integration with Jenkins

This section documents the integration of SonarQube with Jenkins to perform **static code analysis** and enforce code quality standards within the CI pipeline.

---

## 📌 What is SonarQube?

SonarQube is a platform used for **continuous inspection of code quality**.

It analyzes code for:
- Bugs
- Vulnerabilities (security issues)
- Code smells
- Test coverage
- Maintainability issues

---

## 🧱 Infrastructure Setup

### 🔹 EC2 Instance
- OS: Ubuntu
- Instance Type: t2.medium

### 🔹 Ports
- Internal: `9000` (SonarQube)
- External: `80` (via Nginx reverse proxy)

---

## ⚙️ SonarQube Setup Highlights

- Installed Java 21
- Installed PostgreSQL database
- Created:
  - Database: `sonarqube`
  - User: `sonar`
- Configured `sonar.properties`
- Setup systemd service
- Configured Nginx reverse proxy

---

## 🔗 Jenkins Integration

### Step 1: Install Plugin
- SonarQube Scanner Plugin

---

### Step 2: Configure SonarQube Server in Jenkins

```
Manage Jenkins → Configure System → SonarQube Servers
```

Add:
- Name: `sonarserver`
- Server URL: `http://<SONAR_PUBLIC_IP>`
- Authentication Token (generated in SonarQube)

---

### Step 3: Add Scanner Tool

```
Manage Jenkins → Global Tool Configuration
```

Add:
- Name: `sonar8.0`
- Type: SonarQube Scanner

---

## 🔑 Token Generation (SonarQube)

- Login to SonarQube UI
- Go to:
```
My Account → Security → Generate Token
```
- Add this token in Jenkins credentials

---

## 📜 Pipeline Integration

### SonarQube Analysis Stage

```groovy
stage('Sonar Code analysis') {
  environment {
    scannerHome = tool 'sonar8.0'
  }

  steps {
    withSonarQubeEnv('sonarserver') {
      sh '''${scannerHome}/bin/sonar-scanner \
        -Dsonar.projectKey=vprofile \
        -Dsonar.projectName=vprofile \
        -Dsonar.projectVersion=1.0 \
        -Dsonar.sources=src/ \
        -Dsonar.java.binaries=target/classes \
        -Dsonar.junit.reportsPath=target/surefire-reports \
        -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml \
        -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml'''
    }
  }
}
```

---

## 🔍 Analysis Flow

```
Jenkins → Sonar Scanner → SonarQube Server → Dashboard
```

- Jenkins sends analysis data
- SonarQube processes and stores results
- Results visible on dashboard

---

## 📊 What Was Verified

On SonarQube Dashboard:
- Code quality metrics
- Number of bugs
- Security vulnerabilities
- Coverage reports
- Code smells

---

## ⚠️ Common Issues & Fixes

### 🔸 SonarQube Not Accessible
- Fixed using Nginx reverse proxy

### 🔸 Authentication Failure
- Resolved by correct token configuration

### 🔸 Wrong Paths
- Ensured correct:
  - `sonar.sources`
  - `sonar.java.binaries`

---

## 🧠 Key Learnings

- Code quality must be part of CI pipeline
- Static analysis helps detect issues early
- SonarQube integrates seamlessly with Jenkins
- Reports provide actionable insights

---

## 📊 Outcome

- Successfully integrated SonarQube with Jenkins
- Automated code analysis in pipeline
- Verified results on SonarQube dashboard

---

## 📌 Next Step

- Quality Gates (fail pipeline on bad code)
- Enforcing quality standards

---
