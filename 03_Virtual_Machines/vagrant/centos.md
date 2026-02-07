# Automated CentOS VM Using Vagrant

## Overview
This document covers the **automation of a CentOS virtual machine** using Vagrant.

CentOS is chosen as the documented operating system because it closely aligns with enterprise and server-side Linux environments.

Although Ubuntu was also used during manual VM practice, only CentOS is documented here to keep the repository focused and non-redundant.

---

## Why Automate CentOS
- Represents enterprise Linux systems
- Common in production environments
- Aligns with RHEL-based infrastructure
- Ideal for learning server automation

---

## Vagrant Box Used
- **Box:** CentOS (from Vagrant Cloud)
- **Provider:** VirtualBox

Vagrant boxes are preconfigured images that eliminate the need for manual OS installation.

---

## Project Setup
1. Create a project directory
2. Initialize Vagrant
3. Define VM configuration in `Vagrantfile`
4. Start the VM using Vagrant commands

---

## Example Workflow

```bash
vagrant init
vagrant up
vagrant ssh
