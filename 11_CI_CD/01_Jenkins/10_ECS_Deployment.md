# 🚀 Continuous Deployment using AWS ECS

This section covers deploying Docker images from AWS ECR to AWS ECS, completing the transition from CI to full CI/CD.

---

## 📌 Objective

Extend the pipeline to:
- Deploy containerized application
- Automate service updates
- Achieve continuous deployment (CD)

---

## 🔁 Full CI/CD Flow

```
GitHub → Jenkins → Build → Test → SonarQube → Quality Gate
→ Nexus → Docker Build → ECR → ECS Deployment
```

---

## 🧱 AWS ECS Setup

### 🔹 Step 1: Create ECS Cluster

- Cluster Name: `vprofile-dmn`
- Launch Type: Fargate / EC2

---

### 🔹 Step 2: Create Task Definition

Configured:
- Container Image:
```
<ECR_URL>/vprofileappimg:latest
```

- Port mappings
- CPU & memory allocation

---

### 🔹 Step 3: IAM Role

Attached:
```
CloudWatchLogsFullAccess
```

Used for:
- Logging
- ECS execution permissions

---

### 🔹 Step 4: Create Service

Configured:
- Cluster: `vprofile-dmn`
- Service Name: `vproapptask-service`
- Load Balancer:
  - Target Group
  - Listener

Created new Security Group:
```
vproappEcsElb-SG
```

---

## 🌐 Application Access

After deployment:

- Copied **Load Balancer DNS**
- Opened in browser
- Verified application login page

---

## 📜 Jenkins Pipeline Integration

### ECS Deployment Stage

```groovy
stage('Deploy to ECS') {
  steps {
    withAWS(credentials: 'awscreds', region: 'us-east-1') {
      sh 'aws ecs update-service --cluster ${cluster} --service ${service} --force-new-deployment'
    }
  }
}
```

---

## 🔍 How Deployment Works

1. New image pushed to ECR
2. ECS service triggered for new deployment
3. ECS pulls latest image
4. New tasks started
5. Old tasks terminated (rolling update)

---

## 🧪 Verification

Checked in AWS ECS Console:

- Service events:
```
deployment completed
service reached steady state
```

- Application accessible via Load Balancer

---

## ⚠️ Common Issues & Fixes

### 🔸 Service Not Updating
- Used:
```
--force-new-deployment
```

---

### 🔸 Task Failures
- Checked CloudWatch logs
- Verified container configuration

---

### 🔸 Permission Issues
- Ensured IAM role has required permissions

---

## 🧠 Key Learnings

- ECS enables scalable container deployment
- CI/CD pipelines should automate deployment
- Rolling updates prevent downtime
- Integration with ECR simplifies deployment flow

---

## 📊 Outcome

- Successfully deployed Docker container using ECS
- Integrated ECS deployment into Jenkins pipeline
- Achieved end-to-end CI/CD automation

---

## 📌 Next Step

- Job Triggers (automation on events)
- Fully automated pipelines using GitHub webhooks

---
