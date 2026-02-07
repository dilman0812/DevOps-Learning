# Virtual Machines – DevOps Learning

## Overview
Virtual Machines (VMs) are a core building block of DevOps and cloud infrastructure.  
Before moving into automation, containers, or cloud services, it is essential to understand how virtual machines are created, configured, networked, and accessed **manually**.

This directory documents my hands-on learning of virtual machines using a local hypervisor, with a strong focus on fundamentals that directly translate to real-world DevOps environments.

---

## DevOps Thumb Rule
> **If you want to automate something, you must first know how to do it manually.**

In DevOps, automation is not a replacement for understanding—it is an extension of it.  
Poor automation often comes from skipping the manual phase.

For this reason, virtual machines in this section were:
- Created manually
- Installed step by step
- Networked and accessed without automation tools

Automation will be introduced only after these fundamentals are clearly understood.

---

## Virtualization Environment
- **Hypervisor:** Oracle VirtualBox  
- **Hypervisor Type:** Type 2 (Hosted Hypervisor)  
- **Host Operating System:** Windows  

Oracle VirtualBox provides a practical environment to understand virtualization concepts such as isolation, resource allocation, and networking.

---

## Virtual Machines Managed
Two virtual machines were created and managed manually for learning purposes:

| VM Name     | Operating System | Status |
|------------|------------------|--------|
| `centosvm` | CentOS Stream 9  | Fully documented |
| `ubuntuvm` | Ubuntu Linux     | Used for practice only |

While both VMs were managed manually, **only CentOS is documented in detail** in this repository.  
This decision was made to avoid duplication, as the core VM concepts remain the same across Linux distributions.

---

## Why CentOS Is Documented
CentOS Stream 9 was chosen as the primary documented VM because:
- It represents enterprise Linux environments
- It closely aligns with RHEL-based production systems
- It is commonly encountered in server and cloud workloads

Once the workflow is understood for one Linux distribution, it can be easily replicated for others.

---

## What Is Covered
The CentOS VM documentation includes:
- Manual VM creation
- OS installation
- Bridged networking configuration
- IP discovery using `ip addr show`
- Remote access using SSH
- Verification of remote connectivity

This mirrors how real servers are provisioned and accessed in production.

---

## Repository Structure
```text
Virtual-Machines/
├── README.md
├── centos/
│   ├── README.md
│   ├── installation.md
│   ├── networking.md
│   └── ssh.md
```
