# Automated Website Provisioning on CentOS Using Vagrant

## Overview
This document describes the automated provisioning of a static website on a CentOS Stream 9 virtual machine using Vagrant.

All automation implemented here is a direct conversion of the manual steps previously performed:
- Installing Apache (httpd)
- Deploying an HTML website template
- Managing services
- Accessing the website via VM IP

The goal is to replace manual server setup with repeatable, code-driven automation.

---

## Vagrant Box Details
- Box: eurolinux-vagrant/centos-stream-9
- Operating System: CentOS Stream 9
- Provider: Oracle VirtualBox

Using a Vagrant box eliminates the need for manual OS installation.

---

## Networking Configuration

Private network and public (bridged) network are configured in the Vagrantfile:

    config.vm.network "private_network", ip: "192.168.56.28"
    config.vm.network "public_network"

### Explanation
- Private Network
  - Assigns a static IP address
  - Enables predictable access from the host machine
- Public Network (Bridged)
  - Makes the VM appear as a physical machine on the local network
  - Matches real-world server networking behavior

This setup mirrors the networking used during manual VM configuration.

---

## Resource Allocation

Memory is allocated using provider-specific configuration:

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end

### Explanation
OBOBOBOBOB- Allocates 1 GB RAM to the VM
- Prevents excessive host resource usage
OBOBOB- Simulates real server constraints
OBOB
Resource configuration is now defined as code instead of manual hypervisor tuning.

OBOBOB---
OBOBOB
OBOBOB## Automated Provisioning (Shell Script)

OBProvisioning is handled using an inline shell script defined in the Vagrantfile.

Provisioning logic:
OBOBOBOBOBOBOB
    yum install httpd wget unzip vim -y
OBOBOBOBOB    systemctl start httpd
    systemctl enabled httpd
OBOBOBOB    mkdir -p /tmp/finance
    cd /tmp/finance
OB    wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
    unzip -o 2135_mini_finance.zip
OBOBOBOBOBOBOBOB    cp -r 2135_mini_finance/* /var/www/html/
    systemctl restart httpd
OBOB    cd /tmp/
    rm -rf /tmp/finance
OBOBOBOBOB
### What This Automates
- Installs required packages:
OBOB  - Apache (httpd)
  - wget, unzip, vim
OBOBOBOB- Starts and enables the Apache service
- Downloads an HTML website template
OBOBOB- Deploys website files to /var/www/html
OBOB- Restarts Apache to apply changes
- Cleans up temporary files
OBOB
These steps are identical to the manual setup, now executed automatically during VM creation.
OBOBOB
---
OB
## Website Deployment Details
- Web Server: Apache (httpd)
- Document Root: /var/www/html
- Template Source: Tooplate – Mini Finance
- Access Method: Browser using VM IP address
OB
Once vagrant up completes, the website is immediately available without any manual intervention.
OBOB
---
OB
OBOBOBOBOBOB## End-to-End Automation Flow
OBOB1. vagrant up is executed
2. CentOS VM is created from the Vagrant box
OBOBOB3. Networking and memory are configured
4. Apache is installed and started
OBOBOBOB5. Website template is downloaded and deployed
OBOBOB6. Website becomes accessible via browser
OBOBOB
No SSH login is required at any stage.

---
OAOAOAOA
## Manual vs Automated Comparison

OBManual Setup:
OBOBOBOBOBOBOBOB- SSH into VM
- Install packages manually
OBOBOB- Copy website files manually
- Inconsistent results
OBOBOBOBOBOBOBOB
Vagrant Automation:
OBOBOBOBOBOB- Fully automated
- Scripted provisioning
- Automated deployment
OBOB- Repeatable and consistent

---
OBOBOBOBOBOBOB
## DevOps Learning Outcome
OBOBOBOBOBThis setup demonstrates:
- Infrastructure as Code (IaC)
OBOBOBOB- Automated server provisioning
- Service deployment through configuration
OBOBOBOBOBOB- Reproducible environments

These same principles apply directly to cloud VM provisioning, CI/CD pipelines, and configuration management tools.

---

