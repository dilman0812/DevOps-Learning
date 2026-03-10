# AWS Fundamentals – DevOps Learning

---

## Overview

This section documents hands-on exploration of core AWS services as part of my **DevOps learning journey**.

The focus of this phase was understanding how cloud infrastructure works in practice by deploying and managing real resources instead of only studying concepts.

The experiments covered:

- Compute infrastructure
- Storage systems
- Load balancing
- Monitoring and alerting
- Auto-scaling infrastructure
- Object storage and static website hosting
- Managed databases
- Operational tooling for cloud management

All resources were **created, tested, and cleaned up** after experiments to maintain cost awareness and good cloud practices.

---

## AWS Services Explored

| Category | Services |
|--------|---------|
| Compute | EC2 |
| Storage | EBS, EFS, S3 |
| Load Balancing | Elastic Load Balancing |
| Scaling | Auto Scaling Groups |
| Monitoring | CloudWatch |
| Databases | RDS |
| Management Tools | AWS CLI, Systems Manager, CloudShell |

---

## Hands-on Labs Performed

### EC2 Web Server Deployment

- Launched EC2 instances
- Connected using SSH
- Installed and configured Apache (`httpd`)
- Hosted a website template on the instance

Commands used:

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### Load Balancing

Implemented an **Application Load Balancer** to distribute traffic across multiple EC2 instances.

Architecture tested:

```
User
  |
Load Balancer
  |
EC2 Instance A
EC2 Instance B
EC2 Instance C
```

Observed traffic distribution across instances when refreshing the load balancer endpoint.

---

### Auto Scaling

Configured an **Auto Scaling Group** integrated with a load balancer.

Features tested:

- Launch templates
- Automatic instance provisioning
- Instance replacement on failure
- Integration with load balancer target groups

Test scenario:

```
Terminate instance
      |
ASG launches new instance
      |
Instance joins load balancer
```

This demonstrated **self-healing infrastructure**.

---

### Monitoring with CloudWatch

Explored infrastructure monitoring using **CloudWatch metrics and alarms**.

Experiment performed:

1. Installed the `stress` tool on an EC2 instance.
2. Generated artificial CPU load.
3. Monitored `CPUUtilization` metric.
4. Created an alarm triggered by high CPU usage.

Command used to simulate load:

```bash
stress --cpu 2 --timeout 300
```

---

### S3 Object Storage

Explored core S3 features including:

- Bucket and object structure
- Access control mechanisms
- Versioning
- Lifecycle rules
- Replication configuration

Observed how versioning protects objects from accidental deletion.

---

### Static Website Hosting with S3

Deployed a static website using S3.

Setup included:

- Website bucket for static files
- Logging bucket for access logs
- Static website hosting configuration
- Public access configuration

Architecture:

```
User
  |
S3 Static Website Endpoint
  |
HTML / CSS / JS files
```

Versioning was tested by uploading multiple versions of `index.html`.

---

### Amazon RDS

Explored managed relational databases using Amazon RDS.

Topics studied:

- Database engine selection
- Automated backups
- Snapshots
- Multi-AZ deployments
- Read replicas

Typical architecture:

```
Application Server (EC2)
        |
        |
[O     Amazon RDS
```

---

### AWS Management Tools

Explored tools used for managing infrastructure:

#### AWS CLI

Used for interacting with AWS services via terminal commands.

Example:

```bash
aws ec2 describe-instances
```

#### Systems Manager (SSM)

Learned how **Session Manager** enables secure instance access without SSH.

Benefits:

- No exposed SSH ports
- Centralized access control
- Secure instance management

#### CloudShell

Used AWS CloudShell for browser-based CLI access without local installation.

---

## Key Concepts Learned

- Cloud infrastructure provisioning
- High availability architecture
- Horizontal scaling
- Infrastructure monitoring
- Storage lifecycle management
- Secure remote infrastructure access

---

## Directory Structure

```
09_AWS
│
├── 01_Cloud_Computing_and_AWS_Basics.md
├── 02_EC2_and_EBS.md
├── 03_Load_Balancing_ELB.md
├── 04_Auto_Scaling_Group.md
├── 05_CloudWatch_Monitoring.md
├── 06_S3_Object_Storage.md
├── 07_S3_Static_Website_Hosting.md
├── 08_RDS_Managed_Databases.md
└── 09_AWS_CLI_SSM_CloudShell.md
```

Each document contains notes and observations from the hands-on experiments.

---

## Outcome

By completing these labs, I gained practical experience with the foundational AWS services used in cloud infrastructure.

The exercises demonstrated how cloud systems support:

- scalable application architectures
- automated infrastructure management
- observability and monitoring
- secure remote operations

This phase established a strong foundation for the next stages of the DevOps learning journey.
