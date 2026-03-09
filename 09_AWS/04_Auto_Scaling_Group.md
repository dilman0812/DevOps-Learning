# Auto Scaling Groups (ASG)

---

## Introduction

`Amazon EC2 Auto Scaling` automatically adjusts the number of EC2 instances in response to traffic demand.

Auto Scaling helps maintain:

- High availability
- Fault tolerance
- Cost efficiency
- Elastic infrastructure

Instead of manually launching or terminating servers, Auto Scaling dynamically manages instance capacity.

Example architecture:

```
Users
   |
Application Load Balancer
   |
Auto Scaling Group
   |
-----------------------
|          |          |
EC2        EC2        EC2
```

---

## Key Components of Auto Scaling

### Launch Template

A `Launch Template` defines how new EC2 instances should be created.

It includes configuration such as:

- AMI
- Instance type
- Key pair
- Security group
- Storage configuration
- User data scripts

Example `user data` script used to configure a web server automatically:

```bash
#!/bin/bash
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
echo "Server: $(hostname)" > /var/www/html/index.html
```

This ensures that every new instance launched by the Auto Scaling Group is automatically configured as a web server.

---

### Desired Capacity

Defines how many instances should be running normally.

Example:

| Setting | Value |
|-------|-------|
Minimum Capacity | 2 |
Desired Capacity | 2 |
Maximum Capacity | 5 |

The Auto Scaling Group maintains the desired capacity automatically.

---

### Scaling Policies

Scaling policies define when instances should be added or removed.

Common metrics used for scaling include:

- CPU utilization
- Network traffic
- Request count

Example scaling rule:

```
CPU Utilization > 70% → Launch new instance
CPU Utilization < 30% → Terminate instance
```

These policies often rely on metrics collected by CloudWatch.

---

## Integration with Load Balancer

Auto Scaling Groups are typically attached to a load balancer.

Architecture:

```
Client
  |
Application Load Balancer
  |
Target Group
  |
Auto Scaling Group
  |
EC2 Instances
```

The load balancer distributes traffic across healthy instances created by the Auto Scaling Group.

---

## Self-Healing Infrastructure

One major benefit of Auto Scaling is **automatic instance replacement**.

If an EC2 instance fails or is terminated:

```
Instance Failure
      |
ASG detects capacity drop
      |
New EC2 instance launched
      |
Instance registered to load balancer
```

This ensures application availability without manual intervention.

---

## Hands-on: Implementing Auto Scaling

To understand dynamic scaling behavior, the following steps were performed.

### Steps Performed

1. Launched EC2 instances configured as web servers.
2. Created a Launch Template.
3. Created an Auto Scaling Group.
4. Attached the Auto Scaling Group to a Target Group.
5. Integrated the Target Group with an Application Load Balancer.

User data was used to automatically configure the web server during instance launch.

---

## Testing Instance Replacement

To observe self-healing behavior:

1. An instance in the Auto Scaling Group was manually terminated.
2. The Auto Scaling Group detected the reduction in capacity.
3. A new instance was automatically launched.
4. The new instance was registered with the load balancer.

This demonstrated automatic recovery and infrastructure resilience.

---

## Benefits of Auto Scaling

### Elastic Infrastructure

Resources scale based on demand.

### High Availability

Applications remain available even if instances fail.

### Cost Optimization

Unused instances are automatically removed during low traffic periods.

### Automated Recovery

Failed instances are replaced automatically.

---

## Key Takeaways

During the Auto Scaling hands-on lab:

- Created a Launch Template
- Configured an Auto Scaling Group
- Integrated Auto Scaling with an Application Load Balancer
- Implemented automatic instance provisioning
- Observed self-healing infrastructure behavior

This experiment demonstrated how cloud infrastructure can dynamically scale and maintain availability under varying workloads.
