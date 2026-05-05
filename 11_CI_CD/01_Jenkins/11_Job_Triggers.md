# ⏱️ Jenkins Job Triggers

This section covers different ways to automatically trigger Jenkins jobs based on events, schedules, or external requests.

---

## 📌 Why Job Triggers are Important

Job triggers enable:
- Fully automated CI/CD pipelines
- Event-driven builds
- Reduced manual intervention
- Faster feedback loops

---

## 🔁 Types of Triggers Implemented

- GitHub Webhook Trigger
- Poll SCM
- Scheduled Jobs
- Remote Trigger (API-based)
- Build After Other Projects

---

## 🔗 1. GitHub Webhook Trigger

### 📌 Concept
Triggers Jenkins job immediately when code is pushed to GitHub.

---

### ⚙️ Setup Steps

1. Go to GitHub Repository → Settings → Webhooks
2. Add Webhook:
```
Payload URL: http://<JENKINS_IP>:8080/github-webhook/
Content Type: application/json
Event: Just the push event
```

3. In Jenkins Job:
- Enable:
```
GitHub hook trigger for GITScm polling
```

---

### 🧪 Test

- Pushed new file to GitHub
- Job triggered automatically

---

## 🔄 2. Poll SCM

### 📌 Concept
Jenkins periodically checks for changes in repository.

---

### ⚙️ Setup

In Jenkins Job → Build Triggers:

Enable:
```
Poll SCM
```

Schedule:
```
* * * * *
```

---

### 🧪 Test

- Pushed code
- Job triggered within 1 minute

---

## ⏰ 3. Scheduled Jobs

### 📌 Concept
Runs jobs at predefined times (cron-based scheduling).

---

### ⚙️ Setup

Enable:
```
Build periodically
```

Example:
```
30 20 * * 1-5
```

Meaning:
- 8:30 PM
- Monday to Friday

---

## 🌐 4. Remote Trigger (API-based)

### 📌 Concept
Trigger Jenkins job via HTTP API.

---

### ⚙️ Setup

#### Step 1: Enable Remote Trigger

- Job → Configure → Build Triggers
- Enable:
```
Trigger builds remotely
```
- Set token:
```
testtoken
```

---

#### Step 2: Generate API Token

- Jenkins → User → Configure
- Generate API token

Example:
```
admin:API_TOKEN
```

---

#### Step 3: Generate Crumb

```bash
wget -q --auth-no-challenge --user username --password password \
--output-document - \
'http://<JENKINS_IP>:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'
```

---

#### Step 4: Trigger Build

```bash
curl -I -X POST http://username:APItoken@<JENKINS_IP>:8080/job/<JOB_NAME>/build?token=testtoken \
-H "Jenkins-Crumb:<CRUMB>"
```

---

## 🔗 5. Build After Other Projects

### 📌 Concept
Trigger a job after another job completes.

---

### ⚙️ Setup

1. Create Job A (example: Build)
2. Create Job B (example: Test Job)

In Job B:

Enable:
```
Build after other projects are built
```

Set:
```
Projects to watch: Build
```

---

### 🧪 Test

- Triggered Job A
- Job B executed automatically after completion

---

## ⚠️ Comparison of Triggers

| Trigger Type | Use Case | Real-Time |
|-------------|--------|----------|
| Webhook | Code push events | ✅ Yes |
| Poll SCM | Backup polling | ❌ Delayed |
| Scheduled | Cron jobs | ❌ Time-based |
| Remote | API-based systems | ✅ Yes |
| Chained Jobs | Pipeline chaining | ✅ Yes |

---

## 🧠 Key Learnings

- Webhooks are preferred for real-time CI
- Poll SCM is fallback when webhooks not possible
- Cron jobs useful for scheduled automation
- Remote triggers enable integration with external systems

---

## 📊 Outcome

- Successfully implemented multiple trigger mechanisms
- Verified automatic job execution in all scenarios
- Enabled fully automated pipeline execution

---

## 📌 Next Step

- Jenkins Security
- User roles and permissions

---
