# SSH Access to CentOS Virtual Machine

## Overview
Secure Shell (SSH) is the primary method used to access and manage Linux servers in real-world DevOps environments. In production systems, servers are accessed remotely using SSH rather than GUI or hypervisor consoles. This document records how SSH access was manually verified for the CentOS virtual machine.

---

## Prerequisites
- CentOS Stream 9 installed and running
- Network adapter configured as Bridged
- SSH service available on the VM
- Linux user account created during installation
- Git Bash installed on the host system (Windows)

---

## SSH Client Used
Git Bash (Windows)

Git Bash provides a Unix-like terminal environment with built-in SSH support, making it suitable for remote Linux access from Windows.

---

## Finding the VM IP Address
After starting the CentOS VM, the following command was executed inside the VM terminal to identify the IP address assigned to the bridged network interface:

```bash
ip addr show
```

---

## SSH Connection Command
From the host machine (Git Bash), the following command was executed:

```bash
ssh username@<centos-vm-ip>
```

Where:
- username is the Linux user created during CentOS installation
- <centos-vm-ip> is the IP address obtained using the ip addr show command

---

## Verifying the Connected Machine
After successfully logging in via SSH, the following command was executed to confirm the hostname of the CentOS virtual machine:

```bash
hostname
```

This confirms that the remote SSH session is connected to the intended CentOS VM.

---

## First-Time Connection Behavior
On the first SSH connection attempt, SSH prompted for host key verification. Accepting the prompt establishes trust with the remote system and protects against man-in-the-middle attacks.

---

## Outcome
- Successful SSH login to the CentOS virtual machine
- Remote access confirmed without using the VirtualBox console
- CentOS VM can now be managed entirely via terminal

---
