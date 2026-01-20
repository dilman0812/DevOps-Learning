# CentOS VM Networking

## Objective
Understand how virtual machine networking works and how a VM obtains an IP address.

---

## Network Mode Used
- **Adapter Type:** Bridged Adapter

Using bridged networking allows the VM to:
- Appear as a separate machine on the local network
- Receive an IP address from the same network as the host
- Be accessed directly via SSH

---

## Finding the IP Address
After starting the CentOS VM, the following command was executed:

```bash
ip addr show
```
