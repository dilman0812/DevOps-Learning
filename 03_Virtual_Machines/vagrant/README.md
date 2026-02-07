# Vagrant – Automated Virtual Machine Management

## Overview
This directory documents my learning and hands-on work with **Vagrant** as part of my DevOps journey.

After manually creating and managing virtual machines, Vagrant was introduced to **automate VM lifecycle management** and move toward **Infrastructure as Code (IaC)**.

The focus here is not just on running commands, but on understanding how **manual server workflows are translated into automation**.

---

## Why Vagrant
Manual VM management becomes inefficient as environments grow:
- Repetitive OS setup
- Manual service installation
- Difficult replication
- Inconsistent environments

Vagrant solves these problems by:
- Using prebuilt VM images (boxes)
- Defining infrastructure in a `Vagrantfile`
- Automating VM creation, networking, and provisioning
- Enabling reproducible environments

This aligns with real-world DevOps practices.

---

## What Is Covered

### 1. Single VM Automation (CentOS)
- Automated CentOS VM creation
- Apache (`httpd`) installation
- Static website deployment
- Service management using provisioning

File:
- `automation-centos-website.md`

---

### 2. Ubuntu LAMP + WordPress (Manual First)
- Ubuntu VM setup
- LAMP stack installation
- WordPress deployment
- Database-backed application hosting

Documented manually first to ensure understanding before automation.

File:
- `ubuntu-lamp-wordpress.md`

---

### 3. Multi-VM Setup Using Vagrant
- Multiple VMs defined in a single Vagrantfile
- Role-based servers:
  - `web01` (Ubuntu)
  - `web02` (Ubuntu)
  - `db01` (CentOS)
- Private networking for all VMs
- Targeted provisioning only for database node
- Hostnames configured per VM

File:
- `multi-vm.md`

---

### 4. Resource, Networking, and Provisioning Concepts
- CPU and RAM configuration
- Private networking
- Synced directories
- Shell provisioning

Files:
- `resources.md`
- `networking.md`
- `sync-directories.md`
- `provisioning.md`

---

### 5. systemd & Tomcat (Manual Learning)
- Manual Tomcat 10 installation on CentOS
- Creation of custom systemd service
- Understanding `systemctl`, service lifecycle, and security practices

This was documented as a **learning exercise**, not automated yet.

File:
- `centos/tomcat-systemctl.md`

---

## Directory Structure

```
vagrant/
├── README.md
├── resources.md
├── networking.md
├── sync-directories.md
├── provisioning.md
├── web-hosting.md
├── automation-centos-website.md
├── ubuntu-lamp-wordpress.md
└── multi-vm.md

```
---

## DevOps Learning Outcome
Through this section, I learned to:
- Move from manual VM management to automation
- Define infrastructure using code
- Provision services automatically
- Model multi-node environments
- Understand service management with systemd

These skills directly map to:
- Cloud virtual machines
- Configuration management tools
- CI/CD infrastructure
- Scalable DevOps environments

---
