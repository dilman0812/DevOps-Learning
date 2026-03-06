# Cloud Computing & AWS Basics

## What is Cloud Computing?

Cloud computing is the on-demand delivery of computing services such as servers, storage, databases, networking, and software over the internet.

Instead of managing physical hardware, cloud providers allow users to provision infrastructure and services dynamically.

Key characteristics of cloud computing:

- On-demand self service
- Broad network access
- Resource pooling
- Rapid elasticity and scalability
- Pay-as-you-go pricing model

---

## Cloud Service Models

### Infrastructure as a Service (IaaS)

Provides virtualized computing resources over the internet.

Examples:
- AWS EC2
- AWS EBS
- AWS VPC

Users manage:
- OS
- Applications
- Runtime
- Data

---

### Platform as a Service (PaaS)

Provides a platform for building and deploying applications without managing infrastructure.

Examples:
- AWS Elastic Beanstalk
- Google App Engine
- Heroku

Users manage:
- Application code
- Data

---

### Software as a Service (SaaS)

Provides fully managed software applications over the internet.

Examples:
- Gmail
- Salesforce
- Slack

Users only interact with the application.

---

## Why Cloud is Important for DevOps

Cloud platforms enable DevOps practices by providing:

- Rapid infrastructure provisioning
- Scalable environments
- Automation capabilities
- Infrastructure as code
- Integrated monitoring and logging

This allows teams to deploy and scale applications quickly without managing physical hardware.

---

## Introduction to AWS

Amazon Web Services (AWS) is a cloud computing platform that provides a wide range of infrastructure and platform services.

Common AWS service categories include:

| Category | Services |
|--------|--------|
| Compute | EC2, Lambda |
| Storage | S3, EBS, EFS |
| Networking | VPC, ELB |
| Databases | RDS, DynamoDB |
| Monitoring | CloudWatch |

AWS operates globally across multiple regions and availability zones to ensure high availability and fault tolerance.

---

## AWS Global Infrastructure

AWS infrastructure consists of:

### Regions

A region is a physical geographic area containing multiple data centers.

Example:
- us-east-1
- ap-south-1

### Availability Zones (AZ)

Each region contains multiple isolated data centers called Availability Zones.

Benefits:
- Fault isolation
- High availability
- Disaster recovery

Example architecture:

User → Load Balancer → Multiple EC2 Instances across AZs

---

## Hands-on Observations

During the AWS lab work:

- Explored AWS console and service categories
- Launched EC2 instances to host web servers
- Configured load balancers and auto scaling
- Monitored infrastructure using CloudWatch
- Hosted static websites using S3

These experiments demonstrated how cloud infrastructure can be provisioned, scaled, and monitored dynamically.
