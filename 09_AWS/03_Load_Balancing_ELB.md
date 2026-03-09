# Elastic Load Balancing (ELB)

---

## Introduction

`Elastic Load Balancing (ELB)` automatically distributes incoming application traffic across multiple compute resources such as EC2 instances.

Load balancing improves:

- High availability
- Fault tolerance
- Application scalability

Instead of sending all requests to a single server, a load balancer distributes requests across multiple instances.

Example architecture:

```
Client
   |
Load Balancer
   |
---------------------
|        |         |
EC2      EC2       EC2
```

---

## Types of AWS Load Balancers

AWS provides multiple load balancing solutions.

| Load Balancer | Layer | Use Case |
|---------------|------|----------|
| Application Load Balancer (ALB) | Layer 7 | HTTP / HTTPS traffic |
| Network Load Balancer (NLB) | Layer 4 | TCP / UDP traffic |
| Gateway Load Balancer | Layer 3 | Security appliances |

For web applications, the **Application Load Balancer (ALB)** is most commonly used.

---

## Application Load Balancer (ALB)

`Application Load Balancer` operates at **Layer 7 (Application Layer)** of the OSI model.

It can route traffic based on:

- URL paths
- Hostnames
- HTTP headers

Example:

```
example.com/api → Backend API servers
example.com/web → Web servers
```

This makes ALB useful for **microservices architectures**.

---

## Target Groups

A `Target Group` is used by the load balancer to route traffic to registered resources.

Targets can include:

- EC2 instances
- IP addresses
- Lambda functions

Example architecture:

```
Client
   |
Application Load Balancer
   |
Target Group
   |
EC2 Instances
```

The load balancer sends traffic only to **healthy targets**.

---

## Health Checks

Health checks allow the load balancer to determine if an instance is functioning correctly.

Typical configuration:

| Parameter | Example |
|----------|---------|
| Protocol | HTTP |
| Path | `/` |
| Interval | 30 seconds |
| Healthy Threshold | 5 |

If an instance fails health checks:

```
Instance becomes unhealthy
       |
Load balancer stops sending traffic
```

---

## Hands-on: Load Balancing EC2 Web Servers

To understand load balancing behavior, multiple EC2 instances were launched and configured as web servers.

### Steps Performed

1. Launched multiple EC2 instances.
2. Installed `httpd` on each instance.
3. Deployed a simple web page showing the server hostname.
4. Created a Target Group.
5. Created an Application Load Balancer.
6. Registered instances with the Target Group.

Example commands used on instances:

```bash
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

To differentiate servers:

```bash
echo "Server: $(hostname)" | sudo tee /var/www/html/index.html
```

---

## Testing Load Balancing

After configuring the load balancer:

- Accessed the **ALB DNS endpoint** from the browser.
- Refreshed the page multiple times.

Observed behavior:

```
Request 1 → EC2 Instance A
Request 2 → EC2 Instance B
Request 3 → EC2 Instance C
```

This confirmed that traffic was being distributed across instances.

---

## Benefits of Load Balancing

Using ELB provides several advantages:

### High Availability

Traffic continues even if one instance fails.

### Scalability

Works seamlessly with Auto Scaling Groups.

### Fault Tolerance

Unhealthy instances are automatically removed from the traffic pool.

### Simplified Traffic Management

Applications can scale horizontally without changing client configuration.

---

## Key Takeaways

During the ELB lab:

- Deployed multiple EC2 web servers
- Configured a Target Group
- Created an Application Load Balancer
- Implemented health checks
- Observed traffic distribution across instances

This demonstrated how load balancing improves application availability and scalability in cloud environments.
