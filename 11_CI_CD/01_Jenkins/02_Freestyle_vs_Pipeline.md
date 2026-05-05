# 🔄 Freestyle vs Pipeline Jobs in Jenkins

This section explores the difference between **Freestyle Jobs** and **Pipeline Jobs**, and why modern CI/CD systems prefer **Pipeline as Code**.

---

## 📌 Freestyle Jobs

Freestyle jobs are the **simplest type of Jenkins jobs**, configured entirely through the Jenkins UI.

### 🔹 Characteristics
- GUI-based configuration
- Easy to set up
- Limited flexibility
- Not version controlled

### 🔹 What I Did

Created a freestyle job and added commands in **Execute Shell**:

```bash
whoami
pwd
id
w
```

Also tested file operations:

```bash
cat /proc/cpuinfo > cpuinfo.txt
ls -ltr
pwd
```

### 🔹 Post-Build Action

Configured artifact archiving:

```
**/*.txt
```

---

## ⚠️ Limitations of Freestyle Jobs

- Not reproducible across environments
- Cannot be version controlled
- Difficult to scale
- Manual configuration prone to errors

---

## 🚀 Pipeline Jobs (Pipeline as Code)

Pipeline jobs define the entire CI/CD workflow using a **Jenkinsfile (code-based configuration)**.

---

## 📜 What is Jenkinsfile?

A `Jenkinsfile` is a script written in **Groovy (Declarative or Scripted syntax)** that defines pipeline stages.

---

## 🔹 Advantages of Pipeline Jobs

- Version controlled (stored in Git)
- Reproducible builds
- Scalable and maintainable
- Supports complex workflows
- Better suited for real-world CI/CD

---

## 🧱 Basic Pipeline Structure

```groovy
pipeline {
    agent any

    stages {
        stage('Stage Name') {
            steps {
                // Commands here
            }
        }
    }
}
```

---

## 🧪 Example Pipeline (Used in Project)

```groovy
pipeline {
    agent any

    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }

    stages {
        stage('Fetch Code') {
            steps {
                git 'https://github.com/hkhcoder/vprofile-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
    }
}
```

---

## 🔁 Key Differences

| Feature | Freestyle Job | Pipeline Job |
|--------|-------------|-------------|
| Configuration | GUI | Code (Jenkinsfile) |
| Version Control | ❌ No | ✅ Yes |
| Flexibility | Limited | High |
| Reusability | Low | High |
| Complexity Handling | Poor | Excellent |

---

## 🧠 Key Learning

- Freestyle jobs are useful for **quick testing**
- Pipeline jobs are essential for **real-world CI/CD systems**
- Jenkinsfile enables **automation, reproducibility, and scalability**

---

## 📊 Outcome

- Understood limitations of GUI-based jobs
- Successfully transitioned to **Pipeline as Code**
- Implemented Jenkinsfile for CI workflows

---

## 📌 Next Step

- Jenkins Agents (Distributed Builds)
- Running jobs on remote nodes

---
