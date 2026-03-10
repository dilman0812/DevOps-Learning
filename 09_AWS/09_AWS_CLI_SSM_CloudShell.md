# AWS CLI, Systems Manager (SSM) and CloudShell

---

## Introduction

Managing cloud infrastructure through graphical interfaces is useful for learning, but production environments typically rely on **command-line tools and automation**.

AWS provides several tools that allow engineers to manage infrastructure efficiently:

- AWS CLI
- AWS Systems Manager (SSM)
- AWS CloudShell

These tools enable remote infrastructure management without direct SSH access to instances.

---

## AWS Command Line Interface (CLI)

`AWS CLI` is a command-line tool that allows users to interact with AWS services directly from the terminal.

Using the CLI, engineers can:

- Launch infrastructure
- Manage storage
- Configure networking
- Automate cloud workflows

The CLI communicates with AWS APIs using configured credentials.

Example command structure:

```bash
aws <service> <operation> <parameters>
```

Example:

```bash
aws ec2 describe-instances
```

This command retrieves information about EC2 instances in the current AWS account.

---

## Configuring AWS CLI

Before using the CLI, credentials must be configured.

Configuration command:

```bash
aws configure
```

Users must provide:

| Parameter | Description |
|----------|-------------|
AWS Access Key ID | Authentication key |
AWS Secret Access Key | Secret authentication key |
Default Region | AWS region for operations |
Output Format | CLI output format (json, table, text) |

Once configured, the CLI can execute commands against AWS resources.

---

## AWS Systems Manager (SSM)

`AWS Systems Manager` provides tools to manage and operate infrastructure at scale.

One of the most useful features is **Session Manager**, which allows remote access to EC2 instances without using SSH.

Benefits of using SSM:

- No need for SSH keys
- No open inbound SSH ports
- Centralized access management
- Session logging and auditing

Architecture example:

```
Administrator
      |
AWS Systems Manager
      |
Managed EC2 Instances
```

Instances must have:

- SSM agent installed
- IAM role allowing SSM access

---

## Session Manager

`Session Manager` allows users to start a shell session directly from the AWS console or CLI.

This enables secure remote management of instances.

Typical workflow:

```
User initiates session
      |
SSM establishes secure connection
      |
Shell access to EC2 instance
```

This approach eliminates the need to expose port `22` to the internet.

---

## AWS CloudShell

`AWS CloudShell` is a browser-based terminal provided by AWS.

It allows users to run AWS CLI commands directly from the AWS console without installing any tools locally.

Features include:

- Pre-installed AWS CLI
- Persistent home directory storage
- Secure browser-based access
- Integrated authentication with AWS console

Example use cases:

- Running CLI commands quickly
- Managing infrastructure scripts
- Troubleshooting AWS resources

---

## Advantages for DevOps

These tools are essential for modern DevOps workflows.

### Automation

CLI tools allow infrastructure operations to be scripted and automated.

### Secure Infrastructure Access

SSM removes the need for SSH access and reduces attack surface.

### Faster Operations

CloudShell enables quick command execution without local setup.

---

## Key Takeaways

During the AWS operational tooling exploration:

- Used AWS CLI to interact with cloud resources
- Explored Systems Manager for remote infrastructure management
- Learned how Session Manager provides secure instance access
- Used CloudShell for browser-based command execution

These tools demonstrate how cloud infrastructure can be managed programmatically and securely without relying on manual console operations.
