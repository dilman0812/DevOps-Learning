# VProfile Local DevOps Stack

This project demonstrates provisioning and running a production-like multi-tier application stack locally using Infrastructure as Code principles.

It was implemented as part of my structured DevOps learning journey to simulate real-world service orchestration and environment reproducibility.

---

## 🔗 Project Repository
https://github.com/dilman0812/vprofile-local-devops-stack

---

## Architecture Overview

The application stack is provisioned using **Vagrant + VirtualBox** and consists of multiple isolated Linux virtual machines communicating over a private network.

### Infrastructure Components

- **Web Tier**
  - Nginx / Apache (reverse proxy)
- **Application Tier**
  - Tomcat-based Java application
- **Database Tier**
  - MySQL
- **Cache Layer**
  - Memcached
- **Message Broker**
  - RabbitMQ

All services run on dedicated VMs and communicate over a controlled private network.

---

## Infrastructure Design Highlights

- Multi-VM provisioning using a single Vagrantfile
- Automated shell provisioning scripts
- Private network configuration for service isolation
- Service dependency management and startup sequencing
- Environment reproducibility with a single `vagrant up`

---

## DevOps Concepts Practiced

- Infrastructure as Code (IaC)
- Local environment parity with production-style architecture
- Linux service management (systemctl, configuration tuning)
- Debugging distributed service connectivity issues
- Log inspection and failure diagnosis
- Dependency orchestration across services

---

## Key Engineering Learnings

- Managing real-world inter-service dependencies
- Troubleshooting database connectivity and port exposure issues
- Understanding service startup ordering constraints
- Configuring application properties for environment-specific deployment
- Building reproducible environments for safe experimentation

---

## Why This Project Matters

This project helped transition from theoretical DevOps concepts to hands-on infrastructure provisioning, multi-service orchestration, and failure debugging in a controlled local environment.

It represents foundational DevOps engineering practice before moving to cloud-based automation and CI/CD workflows.

