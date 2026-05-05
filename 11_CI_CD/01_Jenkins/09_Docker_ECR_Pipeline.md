# 🐳 Docker CI Pipeline with AWS ECR

This section documents the process of containerizing the application using Docker and pushing images to AWS Elastic Container Registry (ECR) as part of the CI pipeline.

---

## 📌 Objective

Extend the CI pipeline to:
- Build Docker images from application artifacts
- Tag images using build metadata
- Push images to AWS ECR

---

## 🔁 Updated CI Flow

```
GitHub → Jenkins → Maven Build → Test → Code Analysis → Docker Build → Push to ECR
```

---

## 🧱 Prerequisites

### 🔹 Jenkins Setup

Installed on Jenkins EC2:
- Docker Engine
- AWS CLI

Added Jenkins user to Docker group:

```bash
sudo usermod -aG docker jenkins
reboot
```

---

### 🔹 AWS Setup

- Created IAM User
- Generated:
  - Access Key
  - Secret Key

- Created ECR Repository:
```
vprofileappimg
```

---

### 🔹 Jenkins Plugins Installed

- Docker Pipeline
- AWS SDK
- Amazon ECR Plugin

---

### 🔹 Credentials Stored in Jenkins

```
ID: awscreds
Type: AWS Credentials
```

---

## 📦 Docker Image Strategy

- Image tagged using:
  - `BUILD_NUMBER`
  - `latest`

Example:
```
vprofileappimg:12
vprofileappimg:latest
```

---

## 📜 Pipeline Implementation

```groovy
pipeline {
    agent any

    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }

    environment {
        registryCredential = 'ecr:us-east-1:awscreds'
        imageName = "020423264252.dkr.ecr.us-east-1.amazonaws.com/vprofileappimg"
        vprofileRegistry = "https://020423264252.dkr.ecr.us-east-1.amazonaws.com"
    }

    stages {

        stage('Fetch Code') {
            steps {
                git branch: 'docker', url: 'https://github.com/hkhcoder/vprofile-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Checkstyle') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('Build App Image') {
            steps {
                script {
                    dockerImage = docker.build(imageName + ":$BUILD_NUMBER", "./Docker-files/app/multistage/")
                }
            }
        }

        stage('Push to ECR') {
            steps {
                script {
                    docker.withRegistry(vprofileRegistry, registryCredential) {
                        dockerImage.push("$BUILD_NUMBER")
                        dockerImage.push('latest')
                    }
                }
            }
        }

        stage('Cleanup Images') {
            steps {
                sh 'docker rmi -f $(docker images -a -q)'
            }
        }
    }
}
```

---

## 🔍 How It Works

1. Build WAR file using Maven
2. Use Dockerfile (multi-stage build)
3. Create container image
4. Authenticate with ECR
5. Push image to registry
6. Clean up local images

---

## 🧪 Verification

- Checked AWS ECR console
- Verified:
  - Image pushed successfully
  - Tags (`BUILD_NUMBER`, `latest`) present

---

## ⚠️ Common Issues & Fixes

### 🔸 Docker Permission Error
Fix:
```bash
usermod -aG docker jenkins
reboot
```

---

### 🔸 ECR Authentication Failure
- Verified AWS credentials in Jenkins
- Checked region configuration

---

### 🔸 Disk Usage High
Fix:
```bash
docker rmi -f $(docker images -a -q)
```

---

## 🧠 Key Learnings

- Docker enables consistent runtime environments
- ECR provides secure image storage
- Image tagging is critical for version control
- CI pipelines should clean up resources

---

## 📊 Outcome

- Successfully built Docker images from CI pipeline
- Pushed images to AWS ECR
- Established foundation for container-based deployment

---

## 📌 Next Step

- Deploy Docker images using AWS ECS
- Extend CI pipeline to CD (Continuous Deployment)

---
