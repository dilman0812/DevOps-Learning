# Amazon S3 Object Storage

---

## Introduction

`Amazon S3 (Simple Storage Service)` is a scalable object storage service used to store and retrieve data from anywhere on the internet.

S3 is designed for:

- High durability
- Scalability
- Data availability
- Cost-efficient storage

Data in S3 is stored as **objects inside buckets**.

Basic structure:

```
Bucket
   |
   |--- Object 1
   |--- Object 2
   |--- Object 3
```

Each object consists of:

- Data
- Metadata
- A unique key (object name)

---

## Key Characteristics of S3

| Feature | Description |
|-------|-------------|
| Durability | 99.999999999% (11 nines) |
| Scalability | Automatically scales with demand |
| Accessibility | Accessible via HTTP/HTTPS APIs |
| Storage Classes | Multiple storage tiers for cost optimization |

S3 is widely used for storing:

- Application assets
- Logs
- Backups
- Static website files
- Data lakes

---

## S3 Buckets

A `bucket` is a container used to store objects.

Important properties:

- Bucket names must be globally unique.
- Buckets are created within a specific AWS region.
- Objects are accessed using unique keys.

Example object path:

```
https://bucket-name.s3.amazonaws.com/file.txt
```

---

## S3 Object Access

By default, objects in S3 are **private**.

Access can be controlled using:

| Access Method | Description |
|--------------|-------------|
| ACL (Access Control List) | Object-level permissions |
| Bucket Policies | Bucket-wide permissions |
| IAM Policies | Permissions assigned to users or roles |

Modern best practice typically favors **IAM policies and bucket policies** instead of ACLs.

Example bucket policy allowing public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```

---

## S3 Versioning

`Versioning` allows multiple versions of the same object to be stored in a bucket.

Example:

```
file.txt (v1)
file.txt (v2)
file.txt (v3)
```

Benefits of versioning:

- Protection from accidental deletion
- Ability to restore previous object versions
- Improved data recovery

When an object is deleted in a versioned bucket, a **delete marker** is created instead of permanently removing the data.

---

## Lifecycle Management

`Lifecycle rules` automate object storage management.

Lifecycle policies can perform actions such as:

- Transition objects to cheaper storage tiers
- Automatically delete old objects

Example lifecycle rule:

| Object Age | Action |
|-----------|-------|
30 days | Move to Standard-IA |
90 days | Move to Glacier |
365 days | Delete object |

Lifecycle management helps optimize storage costs over time.

---

## S3 Replication

Replication automatically copies objects between buckets.

Two types of replication are supported.

| Replication Type | Description |
|-----------------|-------------|
| Same-Region Replication (SRR) | Replicates objects within the same AWS region |
| Cross-Region Replication (CRR) | Replicates objects to another AWS region |

Example replication architecture:

```
Primary Bucket (Region A)
        |
        | replication
        |
Secondary Bucket (Region B)
```

Replication improves:

- Disaster recovery
- Data redundancy
- Geographic distribution of data

---

## Hands-on Exploration

During the S3 lab work:

- Created S3 buckets
- Explored object access permissions
- Observed how objects are private by default
- Tested versioning by uploading and deleting object versions
- Explored lifecycle configuration rules
- Examined replication rule configuration

This hands-on exercise demonstrated how S3 can manage data durability, access control, and long-term storage lifecycle.
