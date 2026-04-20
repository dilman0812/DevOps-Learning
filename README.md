# DevOps Learning Journey

This repository documents my structured journey toward becoming a DevOps Engineer.  
It contains hands-on experiments, infrastructure setups, automation scripts, and conceptual notes covering core DevOps domains.

The goal of this repository is to build strong foundations in:

- Linux systems
- Networking fundamentals
- Infrastructure automation
- Cloud platforms
- Containerization
- CI/CD workflows

All modules are organized progressively, reflecting how DevOps concepts build on top of each other.

---

# Repository Structure

## 01_Linux_Basics
Core Linux concepts and command-line usage required for managing servers.

Topics covered:
- File system navigation
- Permissions and ownership
- Process management
- Package management
- System monitoring commands

---

## 02_Virtualization
Introduction to virtualization concepts and how virtual machines enable infrastructure isolation and reproducibility.

Topics covered:
- Hypervisors
- Virtual machine lifecycle
- Resource allocation
- VM networking basics

---

## 03_Vagrant
Infrastructure provisioning using Vagrant to automate local development environments.

Topics covered:
- Vagrantfile configuration
- Multi-VM provisioning
- Shell provisioning scripts
- Reproducible environments

---

## 04_Projects

Hands-on infrastructure projects implemented to apply DevOps concepts in real-world scenarios.

---

### 1️⃣ VProfile Local DevOps Stack

Multi-tier application stack provisioned locally using Vagrant and VirtualBox to simulate a production-like environment.

**Key Highlights:**
- Multi-VM architecture with isolated services
- Service dependency management and networking
- Infrastructure provisioning using Vagrant
- Debugging distributed system failures

🔗 Repository:  
https://github.com/dilman0812/vprofile-local-devops-stack

---

### 2️⃣ AWS vProfile Lift & Shift Migration

Migration of the same multi-tier application from local infrastructure to AWS using a **Lift & Shift strategy**, transitioning from manually managed VMs to scalable cloud infrastructure.

**Architecture Overview:**
- Application Load Balancer (HTTPS entry point)
- Auto Scaling Group (application tier)
- Private backend services (MySQL, Memcached, RabbitMQ)
- Route 53 for internal service discovery
- S3 for artifact storage

**Key Achievements:**
- Designed production-style AWS architecture
- Implemented network isolation using Security Groups
- Configured HTTPS with ACM and custom domain
- Built self-healing infrastructure using Auto Scaling
- Deployed application using artifact-based workflow

**DevOps Concepts Demonstrated:**
- Cloud infrastructure design (AWS)
- Load balancing and horizontal scaling
- DNS-based service communication
- Secure networking and access control
- Transition from local → cloud environments

🔗 Repository:  
https://github.com/dilman0812/aws-vprofile-lift-and-shift

---

## 05_Variables_JSON_YAML
Configuration fundamentals used across modern DevOps tooling.

Topics covered:
- Linux environment variables
- JSON data structures
- YAML configuration syntax
- Configuration management principles

Examples included for practical understanding.

---

## 06_Networking
Networking concepts required for cloud infrastructure and distributed systems.

Topics covered:
- IP addressing
- Ports and protocols
- DNS resolution
- TCP vs UDP
- Subnetting and CIDR
- NAT and firewalls
- Network troubleshooting tools

---

## 07_Containers_Intro
Introduction to containerization and how containers differ from traditional virtual machines.

Topics covered:
- What containers are
- Container vs virtual machine architecture
- Container runtimes
- Basic container workflow
- Role of containers in modern DevOps pipelines

---

## 08_Bash_Scripting
Automation using Bash scripting for system administration and DevOps workflows.

Topics covered:
- Bash variables
- Conditionals and loops
- Script automation
- System task automation
- Writing reusable shell scripts

Example scripts demonstrate automation of common system operations.

---

## 09_AWS
Introduction to AWS cloud services and infrastructure deployment.

Topics covered:
- AWS fundamentals
- EC2 instance provisioning
- Security groups
- Load balancing
- Auto scaling
- Cloud infrastructure architecture

Hands-on exercises demonstrate deploying scalable cloud infrastructure.

---

# Learning Philosophy

This repository emphasizes:

- **Hands-on experimentation**
- **Infrastructure reproducibility**
- **Practical troubleshooting**
- **Progressive learning of DevOps systems**

Each module builds on previous concepts to simulate real-world infrastructure and operations workflows.

---

# Goal

The objective of this repository is to build a strong foundation in DevOps engineering and cloud infrastructure by combining theoretical understanding with hands-on implementation.
