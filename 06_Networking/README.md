# Networking Fundamentals for DevOps

This module covers core networking concepts required for DevOps, Cloud Engineering, and Infrastructure roles.

The focus is on practical understanding of how systems communicate, how services connect across networks, and how to debug connectivity issues in distributed environments.

---

# 1️⃣ What is Computer Networking?

Computer Networking (CN) is the practice of connecting computing devices to share resources, exchange data, and communicate using standardized protocols.

Modern DevOps systems rely heavily on networking for:

- Service-to-service communication
- Cloud resource connectivity
- Load balancing
- DNS resolution
- Secure access control
- Distributed architectures

---

# 2️⃣ Client–Server Architecture

Most applications follow a client-server model.

- Client → Sends request
- Server → Processes and responds

Example:
Browser → Web Server → Application → Database

Understanding request flow is critical for debugging latency and connectivity issues.

---

# 3️⃣ IP Addresses

An IP address uniquely identifies a device on a network.

### IPv4 Example
```
192.168.1.10
```

### IPv6 Example
```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

---

## Private vs Public IP

| Type | Usage |
|------|--------|
| Private IP | Internal networks (e.g., 192.168.x.x) |
| Public IP | Internet-facing systems |

Common Private Ranges:
- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

---

# 4️⃣ Ports

Ports allow multiple services to run on a single machine.

Common Ports:

| Service | Port |
|----------|------|
| HTTP | 80 |
| HTTPS | 443 |
| SSH | 22 |
| MySQL | 3306 |
| FTP | 21 |
| SMTP | 25 |

If a service is unreachable, port exposure is often the issue.

---

# 5️⃣ OSI Model (Conceptual)

7 Layers:

1. Physical  
2. Data Link  
3. Network  
4. Transport  
5. Session  
6. Presentation  
7. Application  

For DevOps, focus on:

- Network Layer → IP routing
- Transport Layer → TCP/UDP
- Application Layer → HTTP, DNS, FTP

---

# 6️⃣ TCP/IP Model (Practical)

4 Layers:

1. Application
2. Transport
3. Internet
4. Network Access

Most real-world troubleshooting maps to TCP/IP model.

---

# 7️⃣ TCP vs UDP

| Feature | TCP | UDP |
|----------|------|------|
| Reliable | Yes | No |
| Connection-oriented | Yes | No |
| Ordered delivery | Yes | No |
| Speed | Slower | Faster |

---

## TCP 3-Way Handshake

1. SYN  
2. SYN-ACK  
3. ACK  

Ensures reliable connection establishment before data transfer.

---

# 8️⃣ Sockets

A socket = IP Address + Port

Example:
```
192.168.1.10:3306
```

Sockets allow processes to communicate across a network.

---

# 9️⃣ DNS (Domain Name System)

DNS translates domain names into IP addresses.

Example:
```
google.com → 142.250.x.x
```

Common issues:
- DNS resolution failure
- Wrong nameserver
- TTL caching issues

Check using:
```bash
nslookup google.com
dig google.com
```

---

# 🔟 HTTP Methods

| Method | Purpose |
|--------|----------|
| GET | Retrieve data |
| POST | Create data |
| PUT | Update data |
| DELETE | Remove data |

---

# 1️⃣1️⃣ Routing

Data travels:

Source → Router → Router → Destination

Routing Types:
- Static Routing
- Dynamic Routing

Cloud environments heavily rely on dynamic routing.

---

# 1️⃣2️⃣ Subnetting & CIDR

CIDR example:
```
192.168.1.0/24
```

/24 means:
- 24 bits for network
- 8 bits for hosts
- 256 total addresses

Subnetting allows efficient IP allocation.

---

# 1️⃣3️⃣ NAT (Network Address Translation)

NAT allows private IP addresses to access the internet using a public IP.

Common in:
- Home routers
- Cloud VPCs

---

# 1️⃣4️⃣ Firewalls

Firewalls control inbound and outbound traffic based on rules.

Cloud Equivalent:
- Security Groups
- Network ACLs

Misconfigured firewall rules are a common cause of service failures.

---

# 1️⃣5️⃣ Multiplexing & Demultiplexing

Transport layer manages multiple simultaneous connections using ports.

Allows:
- Multiple applications
- Single IP address

---

# 1️⃣6️⃣ Essential Networking Debugging Commands

```bash
ping
traceroute
netstat
ss
curl
telnet
nc
nmap
```

Examples:

```bash
ping 8.8.8.8
curl http://localhost:8080
netstat -tulnp
```

---

# DevOps Relevance

Networking knowledge is critical for:

- Debugging microservices
- Configuring load balancers
- Managing cloud VPCs
- Exposing services securely
- Database connectivity troubleshooting
- Understanding container networking

Without networking fundamentals, DevOps troubleshooting becomes guesswork.

---

# Key Takeaways

- IP + Port = Socket
- TCP ensures reliability; UDP favors speed
- DNS resolves names to IPs
- Firewalls control access
- NAT enables internet access for private networks
- Subnetting controls network segmentation
- Networking issues are among the most common production failures

