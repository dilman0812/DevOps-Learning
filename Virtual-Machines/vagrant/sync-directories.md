# Synced Directories in Vagrant

## Overview
In DevOps workflows, application code typically lives on the **host machine** while it is executed inside a **server environment**.

Vagrant synced directories allow files to be **shared automatically** between the host system and the virtual machine, eliminating manual file transfer.

---

## Why Synced Directories Matter
Without synced directories:
- Code must be copied manually into the VM
- Changes require repeated file transfers
- Development workflows become slow and error-prone

Synced directories enable:
- Real-time file synchronization
- Faster development iterations
- Clean separation between code and infrastructure

---

## Default Synced Directory
By default, Vagrant syncs:
- Project directory on the host  
to  
- `/vagrant` directory inside the VM

This means:
- Files created on the host appear inside the VM
- Files created inside the VM appear on the host

No additional configuration is required for basic usage.

---

## Custom Synced Directory Configuration
Custom directories can be configured in the `Vagrantfile`.

Example:

```ruby
config.vm.synced_folder "./app", "/var/www/html"

