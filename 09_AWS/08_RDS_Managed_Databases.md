# Amazon RDS Managed Databases

---

## Introduction

`Amazon RDS (Relational Database Service)` is a managed database service that simplifies the setup, operation, and scaling of relational databases in the cloud.

RDS removes the need to manually manage database infrastructure such as:

- Hardware provisioning
- Operating system maintenance
- Database patching
- Backups
- High availability configuration

This allows engineers to focus on application development rather than database administration.

---

## Supported Database Engines

Amazon RDS supports multiple relational database engines.

| Database Engine | Description |
|----------------|-------------|
| MySQL | Popular open-source relational database |
| PostgreSQL | Advanced open-source relational database |
| MariaDB | Community-developed MySQL-compatible database |
| Oracle | Enterprise-grade relational database |
| Microsoft SQL Server | Microsoft relational database engine |
| Amazon Aurora | AWS-optimized high-performance database |

Each engine is fully managed by AWS.

---

## RDS Architecture

Typical architecture:

```
Application Server (EC2)
        |
        |
     Amazon RDS
```

In most cloud architectures:

- EC2 instances host application logic.
- RDS stores structured data.

This separation improves scalability and reliability.

---

## RDS Instance Components

When launching an RDS instance, several parameters must be configured.

| Component | Description |
|----------|-------------|
| Database Engine | Type of database system |
| Instance Class | CPU and memory configuration |
| Storage Type | SSD or provisioned storage |
| VPC Configuration | Network placement |
| Security Groups | Control database access |

RDS instances are typically placed inside a **VPC** for network isolation.

---

## Automated Backups

RDS automatically creates backups of databases.

Backup features include:

- Daily snapshots
- Transaction logs
- Point-in-time recovery

Backup retention can be configured from **1 to 35 days**.

Example recovery process:

```
Backup Snapshot
      |
Restore Database Instance
```

This ensures data durability and disaster recovery capability.

---

## Snapshots

`DB Snapshots` are manual backups of an RDS instance.

Characteristics:

- Stored in Amazon S3
- Persist even after the database is deleted
- Can be used to create new database instances

Snapshots are commonly used for:

- Database migrations
- Testing environments
- Backup retention beyond automated backups

---

## Multi-AZ Deployment

`Multi-AZ (Availability Zone)` deployment improves database availability.

Architecture:

```
Primary Database
       |
Synchronous Replication
       |
Standby Database (Different AZ)
```

If the primary database fails:

```
Automatic Failover
       |
Standby becomes primary
```

This provides high availability for production workloads.

---

## Read Replicas

`Read Replicas` improve database read performance.

Architecture:

```
Primary Database
       |
       |
-----------------------
|          |          |
Replica     Replica     Replica
```

Applications can send **read queries** to replicas while **write queries** go to the primary database.

This helps scale read-heavy workloads.

---

## Security in RDS

RDS provides multiple layers of security.

### Network Security

- Databases run inside a VPC
- Security groups restrict access

Example rule:

```
Allow MySQL access on port 3306 from application servers
```

### Encryption

RDS supports encryption for:

- Data at rest
- Data in transit

### IAM Authentication

AWS Identity and Access Management can control database access.

---

## Benefits of RDS

### Managed Infrastructure

AWS manages operating system and database maintenance.

### High Availability

Multi-AZ deployment ensures minimal downtime.

### Scalability

Database instance sizes can be scaled vertically.

### Automated Backups

Continuous backups simplify disaster recovery.

---

## Key Takeaways

Amazon RDS provides a managed relational database platform that simplifies database deployment and management.

Important capabilities include:

- Automated backups and snapshots
- High availability with Multi-AZ deployments
- Read replicas for scaling read operations
- Secure access using VPC and security groups

RDS is commonly used as the database layer in cloud-based application architectures.
