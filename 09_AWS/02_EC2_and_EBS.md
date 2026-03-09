# EC2 and EBS

---

## Amazon EC2

`Amazon EC2 (Elastic Compute Cloud)` provides scalable virtual servers in the cloud.  
It allows users to launch and manage compute instances without maintaining physical hardware.

EC2 instances are commonly used for:

- Hosting web applications
- Running backend services
- Development and testing environments
- Distributed systems and microservices

---

## EC2 Instance Components

When launching an EC2 instance, several components are configured:

| Component | Description |
|----------|-------------|
| AMI | Amazon Machine Image used to create the instance |
| Instance Type | Defines CPU, memory, and network capacity |
| Key Pair | Used for SSH authentication |
| Security Group | Virtual firewall controlling inbound/outbound traffic |
| Storage | Typically provided using EBS volumes |

---

## Connecting to an EC2 Instance

EC2 instances can be accessed using SSH.

Example:

```bash
ssh -i "keypair.pem" ec2-user@<public-ip>
```

Common default usernames:

| OS | Username |
|----|----------|
| Amazon Linux | `ec2-user` |
| Ubuntu | `ubuntu` |
| CentOS | `centos` |

---

## Hands-on: Deploying a Web Server on EC2

To understand cloud infrastructure deployment, an EC2 instance was launched and configured as a basic web server.

### Steps Performed

1. Launched an EC2 instance using Amazon Linux.
2. Connected to the instance via SSH.
3. Installed the Apache HTTP server.
4. Hosted a website template.

Example commands used:

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

The web content was placed in:

```
/var/www/html
```

After configuration, the website was accessed through the instance's **public IP address**:

```
http://<EC2-public-ip>
```

This experiment replicated the same setup previously done using local virtual machines (VirtualBox/Vagrant), but deployed on cloud infrastructure.

---

## Security Groups

A `Security Group` acts as a virtual firewall for EC2 instances.

Common configuration for web servers:

| Protocol | Port | Purpose |
|---------|------|---------|
| SSH | 22 | Remote access |
| HTTP | 80 | Web traffic |
| HTTPS | 443 | Secure web traffic |

Example rule for allowing web traffic:

```
Type: HTTP
Protocol: TCP
Port: 80
Source: 0.0.0.0/0
```

---

## Amazon EBS

`Amazon Elastic Block Store (EBS)` provides persistent block storage for EC2 instances.

EBS volumes behave like physical hard drives attached to virtual machines.

Common characteristics:

- Persistent storage
- High durability
- Can be detached and attached to other instances
- Used for operating systems and application data

---

## EBS Volume Types

| Volume Type | Use Case |
|-------------|----------|
| gp3 | General purpose SSD (most common) |
| io2 | High-performance SSD for databases |
| st1 | Throughput optimized HDD |
| sc1 | Cold storage HDD |

---

## EBS Snapshots

`EBS Snapshots` create point-in-time backups of volumes.

Snapshots are stored in Amazon S3 and can be used to:

- Restore volumes
- Create new volumes
- Backup system state

Typical workflow:

```
EBS Volume → Snapshot → New Volume → Attach to Instance
```

Snapshots are commonly used for disaster recovery and backup strategies.

---

## Key Takeaways

During the EC2 hands-on lab:

- Launched and configured EC2 instances
- Connected to instances using SSH
- Installed and configured an Apache web server
- Hosted a website template on the instance
- Explored EBS volumes and snapshot functionality

This exercise demonstrated how cloud infrastructure can replace locally managed virtual machines for deploying and hosting applications.
