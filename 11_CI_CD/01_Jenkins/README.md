# 🚀 CI/CD Pipeline with Jenkins (AWS-Based DevOps Implementation)

This project documents the implementation of a **production-style CI/CD pipeline** using Jenkins integrated with SonarQube, Nexus Repository, Docker, and AWS services like ECR and ECS.

The goal was to move beyond basic CI and build a **complete automated delivery pipeline** with code quality checks, artifact management, containerization, and deployment.

---

## 📌 Architecture Overview

The CI/CD pipeline follows this flow:

Developer → GitHub → Jenkins  
→ Build (Maven)  
→ Unit Testing  
→ Code Analysis (SonarQube)  
→ Quality Gate  
→ Artifact Upload (Nexus)  
→ Docker Build  
→ Push to AWS ECR  
→ Deploy to AWS ECS  
→ Slack Notifications  

---

## 🔁 CI/CD Pipeline Flow

```
Developer → GitHub → Jenkins Pipeline
        → Fetch Code (Git)
        → Build (Maven)
        → Unit Test
        → Code Analysis (SonarQube)
        → Quality Gate
        → Upload Artifact (Nexus)
        → Build Docker Image
        → Push to AWS ECR
        → Deploy to AWS ECS
        → Notify via Slack
```

---

## 🧱 Infrastructure Setup

### 🔹 Jenkins (Controller)
- Hosted on AWS EC2 (Ubuntu, t2.medium)
- Port: `8080`
- Responsible for pipeline orchestration

### 🔹 Jenkins Agents
- Separate EC2 instance for distributed builds
- Connected via SSH
- Workspace configured at `/opt/jenkins`

### 🔹 SonarQube
- Hosted on EC2 (Ubuntu)
- Runs internally on `9000`
- Exposed via Nginx on `80`

### 🔹 Nexus Repository
- Hosted on EC2 (Amazon Linux)
- Port: `8081`
- Used to store build artifacts

### 🔹 AWS Services
- **ECR** → Container image storage
- **ECS** → Container deployment

---

## ⚙️ Key Features Implemented

### ✅ Continuous Integration
- Automated code fetch from GitHub
- Maven build and unit testing
- Checkstyle analysis
- Static code analysis using SonarQube

### ✅ Quality Control
- Quality Gates enforced via SonarQube
- Pipeline fails if quality thresholds are not met

### ✅ Artifact Management
- WAR artifacts versioned using:
  - `BUILD_ID`
  - `BUILD_TIMESTAMP`
- Stored in Nexus repository

### ✅ Containerization
- Docker multi-stage builds
- Image tagging strategy:
  - `BUILD_NUMBER`
  - `latest`

### ✅ Continuous Deployment
- Docker images pushed to AWS ECR
- ECS service updated using:
```
aws ecs update-service --force-new-deployment
```

### ✅ Notifications
- Slack integration for:
  - Build success
  - Build failure

---

## 🔄 Pipeline as Code

Pipeline implemented using **Jenkinsfile (Declarative Pipeline)**:
- Version controlled
- Reproducible builds
- Environment consistency

---

## 🔌 Integrations

| Tool        | Purpose                     |
|------------|---------------------------|
| GitHub     | Source Code Management     |
| Maven      | Build Tool                 |
| SonarQube  | Code Quality Analysis      |
| Nexus      | Artifact Repository        |
| Docker     | Containerization           |
| AWS ECR    | Image Registry             |
| AWS ECS    | Deployment Platform        |
| Slack      | Notifications              |

---

## ⚡ Jenkins Concepts Covered

- Freestyle vs Pipeline Jobs
- Distributed builds using agents
- Build triggers:
  - Git Webhooks
  - Poll SCM
  - Scheduled jobs
  - Remote triggers
- Plugin ecosystem
- Role-based access control (RBAC)

---

## 🚧 Challenges & Fixes

### 🔸 Disk Space Issue
- Error: `No space left on device`
- Fix: Increased EBS volume from 8GB to 20GB

### 🔸 SonarQube Access
- Fixed using Nginx reverse proxy (port 80 → 9000)

### 🔸 Jenkins Agent Setup
- Fixed permission issues:
```
chown ubuntu:ubuntu /opt/jenkins
```

---

## 📊 Key Learnings

- End-to-end CI/CD pipeline design
- AWS infrastructure setup for DevOps
- Artifact versioning strategies
- Pipeline debugging and failure handling
- Integration of multiple DevOps tools

---

## 🧠 Outcome

Built a **complete CI/CD pipeline** capable of:
- Automating build, test, and deployment
- Enforcing code quality
- Managing artifacts and images
- Deploying applications on AWS ECS

---

## 📌 Next Steps

- GitHub Actions CI/CD
- GitLab CI/CD

---
