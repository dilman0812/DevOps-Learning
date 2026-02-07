
i# Multi-VM Setup Using Vagrant

## Overview
This document describes the creation and understanding of a **multi-VM environment** using **Vagrant**.

Instead of managing a single virtual machine, multiple VMs were defined and launched together using a **single Vagrantfile**, each with a specific role.

This exercise helped in understanding how real-world infrastructures are composed of **multiple interconnected servers**, not just standalone machines.

---

## Virtual Machines Created
The following virtual machines were created as part of the multi-VM setup:

| VM Name | Operating System | Role |
|------|------------------|------|
| web01 | Ubuntu 20.04 | Web server |
| web02 | Ubuntu 20.04 | Web server |
| db01  | CentOS 7 | Database server |

Each VM is defined independently inside the same Vagrantfile.

---

## Networking Configuration
- All virtual machines are connected using a **private network**
- Each VM is assigned a **static IP address**
- VMs can communicate with each other internally

This setup simulates a private data center or cloud subnet where servers communicate over internal IPs.

---

## Hostname Configuration
Each VM has a dedicated hostname:
- `web01`
- `web02`
- `db01`

Setting hostnames helps in:
- Identifying server roles
- Simplifying debugging
- Matching real production server practices

---

## Provisioning
Provisioning was applied **only to the database VM (`db01`)**.

Provisioning actions included:
- Installing MariaDB
- Starting the database service
- Enabling the service at boot

The web servers were intentionally left unprovisioned to focus on:
- Role separation
- Targeted automation
- Understanding selective provisioning

---

## Key Concepts Learned

### Multi-VM Definition
- Multiple VMs can be defined in a single Vagrantfile
- Each VM can have its own OS, network, resources, and provisioning

### Role-Based Infrastructure
- Different servers serve different purposes (web vs database)
- Automation can be applied selectively based on role

### Internal Networking
- Private IPs allow VM-to-VM communication
- Mirrors real production environments

### Targeted Provisioning
- Not all machines need the same configuration
- Provisioning can be applied per VM

---

## DevOps Learning Outcome
This setup demonstrates:
- Multi-node infrastructure modeling
- Infrastructure as Code using Vagrant
- Server role separation
- Realistic environment simulation

These concepts directly apply to:
- Cloud architectures
- Microservices deployments
- CI/CD environments
- Configuration management tools like Ansible

---
