# Virtual Machines – DevOps Learning

## Overview
Virtual Machines (VMs) are a foundational concept in DevOps and cloud computing.  
Before working with automation tools, containers, or cloud platforms, it is essential to understand how virtualized systems behave at the operating system and infrastructure level.

This section documents my **hands-on learning of Virtual Machines**, focusing on **manual setup, configuration, networking, and access**.

---

## DevOps Thumb Rule
> **If you want to automate something, you must first know how to do it manually.**

In DevOps, automation is built on top of understanding.  
Blind automation without manual knowledge leads to fragile systems and poor troubleshooting.

For this reason:
- Virtual machines are created **manually**
- Operating systems are installed **step by step**
- Networking and access are configured **without automation tools**

Automation will be introduced only after these fundamentals are clearly understood.

---

## Virtualization Approach
- **Hypervisor:** Oracle VirtualBox  
- **Hypervisor Type:** Type 2 (Hosted Hypervisor)  
- **Host Operating System:** Windows  

Oracle VirtualBox allows multiple isolated guest operating systems to run on a single physical machine and provides a practical learning environment for virtualization concepts.

---

## Virtual Machines Covered
This section currently includes the following virtual machines:

| VM Name     | Operating System     | Purpose |
|------------|----------------------|--------|
| `centosvm` | CentOS Stream 9      | Enterprise Linux, server-side concepts |
| `ubuntuvm` | Ubuntu Linux         | General Linux usage and DevOps tooling |

Each virtual machine is documented separately with installation steps, networking configuration, and SSH access.

---

## Learning Objectives
Through manual VM management, this section aims to build understanding of:
- Hardware abstraction (CPU, memory, storage)
- OS-level isolation
- Linux distribution differences
- VM networking (NAT vs Bridged)
- Remote access using SSH
- Environment reproducibility

These concepts directly map to real-world DevOps infrastructure.

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
├── ubuntu/
│   ├── README.md
│   ├── installation.md
│   ├── networking.md
│   └── ssh.md
└── comparison/
    └── centos-vs-ubuntu.md
```
