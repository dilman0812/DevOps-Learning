# Ubuntu LAMP Stack with WordPress Using Vagrant

## Overview
This document covers the setup of an **Ubuntu virtual machine** using **Vagrant**, followed by the automated installation of a **LAMP stack** and deployment of a **WordPress website**.

Unlike the CentOS setup (static website), this implementation focuses on a **dynamic, database-backed application**, representing real-world server workloads.

---

## Why Ubuntu for LAMP
Ubuntu is commonly used for:
- Web application hosting
- LAMP stack deployments
- Cloud and production environments

Its strong package ecosystem and community support make it a practical choice for WordPress-based applications.

---

## Virtual Machine Setup
- **OS:** Ubuntu Linux
- **Provider:** Oracle VirtualBox
- **Provisioning Tool:** Vagrant
- **Networking:** Private network with static IP
- **Access:** SSH via `vagrant ssh`

The VM is created and managed entirely through Vagrant.

---

## LAMP Stack Components
The following components are installed via provisioning:

- **Linux:** Ubuntu
- **Apache:** Web server
- **MySQL:** Database server
- **PHP:** Server-side scripting language

These services together enable hosting dynamic PHP-based applications like WordPress.

---

## Automated LAMP Installation
Using shell provisioning, the VM automatically:
- Installs Apache
- Installs MySQL Server
- Installs PHP and required extensions
- Enables and starts required services

This removes the need for manual SSH-based setup.

---

## WordPress Deployment
WordPress is deployed inside the VM by:
- Downloading the WordPress package
- Extracting it to Apache’s document root
- Creating a MySQL database and user
- Configuring file permissions
- Completing setup through the browser

All infrastructure and service setup steps are automated.

---

## Accessing the WordPress Site
Once the VM is running:
- WordPress is accessed via the VM’s private IP address
- The WordPress installation page appears in the browser
- Configuration is completed using the web installer

This confirms:
- Networking is functional
- Apache and PHP are working
- MySQL connectivity is successful

---

## End-to-End Workflow
1. Vagrant creates the Ubuntu VM
2. Provisioning installs LAMP stack
3. WordPress is deployed
4. Website becomes accessible via browser

This demonstrates a complete **infrastructure-to-application** deployment flow.

---

## Manual vs Automated Setup

| Manual Setup | Vagrant Automation |
|-------------|-------------------|
| Manual OS setup | Automated VM creation |
| Manual package installs | Provisioned automatically |
| Manual DB setup | Scripted configuration |
| Time-consuming | Fast and repeatable |

---

## DevOps Learning Outcome
This setup reinforces:
- Multi-service provisioning
- Database-backed application deployment
- Infrastructure automation
- Environment reproducibility

These same concepts apply to:
- Cloud VM deployments
- CI/CD pipelines
- Containerized applications

---

## Next Step
- Parameterize configuration values
- Separate provisioning scripts
- Move toward cloud-based deployments

