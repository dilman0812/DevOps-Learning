# Provisioning in Vagrant

## Overview
Provisioning is the process of **automatically configuring a virtual machine after it is created**.

In DevOps environments, provisioning replaces manual SSH-based setup with **repeatable, automated configuration**, ensuring that every server starts in a known and consistent state.

---

## Why Provisioning Is Needed
Without provisioning:
- Software must be installed manually via SSH
- Configuration steps must be repeated for every VM
- Environments drift over time
- Automation does not scale

Provisioning ensures:
- Consistency across environments
- Faster setup
- Reduced human error
- Infrastructure readiness on boot

---

## What Provisioning Automates
Using provisioning, Vagrant can automatically:
- Install packages
- Configure services
- Execute shell commands
- Prepare the VM for application deployment

All of this happens **without logging into the VM manually**.

---

## Shell Provisioning (Basic Example)
The simplest form of provisioning uses shell commands.

Example in `Vagrantfile`:

```ruby
config.vm.provision "shell", inline: <<-SHELL
  yum update -y
  yum install -y httpd
  systemctl enable httpd
  systemctl start httpd
SHELL

