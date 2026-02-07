# Automated Website Provisioning on CentOS Using Vagrant

## Overview
This document describes the automated provisioning of a static website on a **CentOS Stream 9 virtual machine** using **Vagrant**.

All automation implemented here is a direct conversion of the manual steps previously performed:
- Installing Apache (httpd)
- Deploying an HTML website template
- Managing services
- Accessing the website via VM IP

The goal is to replace manual server setup with **repeatable, code-driven automation**.

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
- **Private Network**
  - Assigns a static IP address
  - Enables predictable access from the host machine
- **Public Network (Bridged)**
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
- Allocates **1 GB RAM** to the VM
- Prevents excessive host resource usage
- Simulates real server constraints

Resource configuration is now defined as code instead of manual hypervisor tuning.

---

## Automated Provisioning (Shell Script)

Provisioning is handled using an **inline shell script** defined in the Vagrantfile.

Provisioning logic:

    yum install httpd wget unzip vim -y
    systemctl start httpd
    systemctl enable httpd
    mkdir -p /tmp/finance
    cd /tmp/finance
    wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
    unzip -o 2135_mini_finance.zip
    cp -r 2135_mini_finance/* /var/www/html/
    systemctl restart httpd
    cd /tmp/
    rm -rf /tmp/finance

### What This Automates
- Installs required packages:
  - Apache (httpd)
  - wget, unzip, vim
- Starts and enables the Apache service
- Downloads an HTML website template
- Deploys website files to `/var/www/html`
- Restarts Apache to apply changes
- Cleans up temporary files

These steps are identical to the manual setup, now executed automatically during VM creation.

---

## Website Deployment Details
- Web Server: Apache (httpd)
- Document Root: `/var/www/html`
- Template Source: Tooplate – Mini Finance
- Access Method: Browser using VM IP address

Once `vagrant up` completes, the website is immediately available without any manual intervention.

---

## End-to-End Automation Flow
1. `vagrant up` is executed
2. CentOS VM is created from the Vagrant box
3. Networking and memory are configured
4. Apache is installed and started
5. Website template is downloaded and deployed
6. Website becomes accessible via browser

No SSH login is required at any stage.

---

## Manual vs Automated Comparison

**Manual Setup**
- SSH into VM
- Install packages manually
- Copy website files manually
- Inconsistent results

**Vagrant Automation**
- Fully automated
- Scripted provisioning
- Automated deployment
- Repeatable and consistent

---

## DevOps Learning Outcome
This setup demonstrates:
- Infrastructure as Code (IaC)
- Automated server provisioning
- Service deployment through configuration
- Reproducible environments

These same principles apply directly to:
- Cloud VM provisioning
- CI/CD pipelines
- Configuration management tools

