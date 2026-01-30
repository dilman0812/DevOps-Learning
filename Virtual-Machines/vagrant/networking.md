# Vagrant VM Networking

## Overview
Networking is a critical part of virtual machine management.  
In DevOps environments, services running inside VMs must be **reachable, predictable, and reproducible**.

This document explains how Vagrant handles VM networking and how network configuration differs from manual VM setups.

---

## Default Networking Behavior (NAT)
By default, Vagrant uses **NAT (Network Address Translation)**.

### What NAT Provides
- VM can access the internet
- No manual network configuration required
- Safe default for basic usage

### Limitations of NAT
- VM is not directly reachable from the host
- Services inside the VM cannot be accessed externally
- Not suitable for hosting applications

NAT is useful for package installation but limited for DevOps workflows.

---

## Private Network (Host-Only)
To allow direct access from the host machine, Vagrant supports **private networking**.

Example configuration in `Vagrantfile`:

```ruby
config.vm.network "private_network", ip: "192.168.56.10"

