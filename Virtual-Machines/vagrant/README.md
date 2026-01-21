# Vagrant – VM Automation

## Overview
After manually creating and managing virtual machines, the next step in my DevOps learning journey is **automating VM lifecycle management**.

This section focuses on **Vagrant**, a tool used to create, configure, and manage virtual machines in a **repeatable and automated way** using configuration files instead of manual steps.

This transition follows a core DevOps principle:
> Manual understanding first, automation second.

---

## Why Vagrant
Manual VM management becomes inefficient when:
- Multiple VMs are required
- Environments must be replicated
- Configuration consistency is critical

Vagrant solves these problems by:
- Eliminating manual OS installation
- Using prebuilt VM images (Vagrant boxes)
- Managing VMs through a single configuration file (`Vagrantfile`)
- Providing CLI-based lifecycle management

---

## What Is Covered Here
This directory documents:
- Vagrant fundamentals
- VM automation using Vagrant
- Automated CentOS VM creation
- VM lifecycle commands
- VM provisioning concepts

Only **CentOS** is documented in detail to avoid duplication, as the same Vagrant workflow applies to other Linux distributions.

---

## Prerequisites
- Virtualization enabled in BIOS
- Oracle VirtualBox installed
- Vagrant installed
- Command-line interface (Git Bash / Terminal)

---

## Directory Structure
```text
vagrant/
├── README.md
└── centos.md
