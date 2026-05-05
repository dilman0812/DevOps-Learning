# 🚦 Quality Gates in CI/CD Pipeline

This section explains how **Quality Gates** in SonarQube are used to enforce code quality by controlling whether a Jenkins pipeline should pass or fail.

---

## 📌 What is a Quality Gate?

A Quality Gate is a set of **conditions applied on code quality metrics** such as:

- Number of bugs
- Security vulnerabilities
- Code coverage
- Code smells

If the conditions are not met:
→ The pipeline **fails or is marked unstable**

---

## 🎯 Why Quality Gates Matter

- Prevent bad code from reaching production
- Enforce coding standards
- Improve security and maintainability
- Automate quality validation

---

## ⚙️ Quality Gate Setup in SonarQube

Created a custom condition:

Example:
- Fail if **Security Issues > 2**

---

## 🔗 Webhook Integration (SonarQube → Jenkins)

To enable real-time communication:

### Step: Create Webhook in SonarQube

```
Name: jenkins-ci-webhook
URL: http://<JENKINS_IP>:8080/sonarqube-webhook
```

This allows SonarQube to send analysis results back to Jenkins.

---

## 📜 Jenkins Pipeline Integration

### Quality Gate Stage

```groovy
stage("Quality Gate") {
    steps {
        timeout(time: 1, unit: 'HOURS') {
            waitForQualityGate abortPipeline: true
        }
    }
}
```

---

## 🔍 How It Works

1. Jenkins runs Sonar analysis
2. SonarQube processes results
3. SonarQube sends status via webhook
4. Jenkins waits for response
5. Pipeline continues or fails

---

## 🧪 Demonstration

- Set condition:
  - Security Issues > 2 → FAIL
- Project had:
  - 3 issues

### Result:
```
Pipeline Status: FAILED
```

Verified:
- Jenkins console output
- SonarQube dashboard

---

## ⚠️ Key Behavior

| Condition | Result |
|----------|-------|
| Quality Gate Passed | Pipeline Continues |
| Quality Gate Failed | Pipeline Aborted |

---

## 🧠 Key Learnings

- CI is incomplete without quality enforcement
- Quality Gates act as **automated checkpoints**
- Webhooks enable real-time pipeline decisions
- Helps maintain production-grade standards

---

## 📊 Outcome

- Successfully configured Quality Gates
- Integrated SonarQube with Jenkins using webhook
- Verified pipeline failure on bad code

---

## 📌 Next Step

- Nexus Integration
- Storing artifacts in centralized repository

---
