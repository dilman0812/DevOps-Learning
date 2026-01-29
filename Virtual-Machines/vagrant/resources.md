# Managing VM Resources with Vagrant (CPU, RAM, IP)

## Overview
In real-world infrastructure, servers are not created with unlimited resources.  
CPU, memory, and network configuration must be **explicitly controlled** to ensure stability, performance, and cost efficiency.

This document covers how Vagrant allows **resource configuration at VM creation time**, removing the need for manual VM tuning.

---

## Why Resource Management Matters
Uncontrolled VM resources can lead to:
- Host system performance degradation
- Unpredictable VM behavior
- Poor simulation of production environments

DevOps workflows require:
- Reproducible resource allocation
- Environment parity across systems
- Infrastructure defined as code

Vagrant enables this through declarative configuration.

---

## Configuring CPU and Memory
CPU and RAM are configured inside the `Vagrantfile`.

Example configuration:

```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = 2048
  vb.cpus = 2
end

