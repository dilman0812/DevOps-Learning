# Hosting a Website on CentOS VM Using Vagrant

## Overview
This document covers the setup of a **static website** on a CentOS virtual machine using **Vagrant provisioning**.

The goal is to demonstrate how infrastructure automation can be used to deploy a running service, moving beyond VM creation into **real server workloads**.

---

## What Was Implemented
Inside the automated CentOS VM:
- Apache HTTP Server (`httpd`) was installed
- The service was enabled and started
- An HTML template was deployed
- The website was accessed via the VM’s IP address

All steps were automated using Vagrant provisioning.

---

## Web Server Used
- **Service:** Apache HTTP Server (`httpd`)
- **Operating System:** CentOS
- **Port:** 80 (default HTTP)

Apache was chosen due to its simplicity and common usage in Linux server environments.

---

## Provisioning the Web Server
The web server installation and startup were automated using shell provisioning.

Example:

```ruby
config.vm.provision "shell", inline: <<-SHELL
  yum install -y httpd
  systemctl enable httpd
  systemctl start httpd
SHELL

