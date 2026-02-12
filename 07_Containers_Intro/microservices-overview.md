# Microservices – Overview (Foundational Level)

---

# 1. What Are Microservices?

Microservices is an architectural style where an application is built as a collection of small, independent services.

Each service:

- Has a specific responsibility
- Runs independently
- Communicates via APIs (commonly HTTP/REST)
- Can be developed and deployed separately

Instead of building one large system, the application is divided into multiple smaller services.

---

# 2. Monolithic vs Microservices Architecture

## Monolithic Architecture

- Single codebase
- Single deployment unit
- All components tightly coupled
- Scaling requires scaling the entire application

## Microservices Architecture

- Multiple small services
- Independent deployment
- Loosely coupled components
- Each service can scale independently

---

# 3. Why Microservices?

Microservices provide:

- Independent scaling
- Faster feature releases
- Better fault isolation
- Team-level ownership of services
- Flexibility in technology choices

Example:

If only the payment service needs high traffic handling, only that service can be scaled — not the entire system.

---

# 4. Microservices and Containerization

Microservices are commonly deployed using containers because:

- Each service can run inside its own container
- Services remain isolated
- Deployment becomes consistent across environments
- Scaling becomes easier

Conceptual example:

User Service → Container  
Order Service → Container  
Payment Service → Container  

All services communicate via APIs.

Containerization ensures that each service includes its own runtime and dependencies.

---

# 5. Basic Understanding from This Phase

In this learning phase, covered:

- What microservices are
- Difference between monolithic and microservices architecture
- Why microservices are used
- How containerization supports microservices
- High-level architectural understanding

---

# 6. Not Covered Yet (To Be Explored Later)

Advanced topics that will be covered in later phases:

- Service communication patterns
- API Gateway
- Service discovery
- Load balancing
- Container orchestration (e.g., Kubernetes)
- Distributed logging and monitoring
- Production-level microservices deployment

---

# Summary

Microservices is an architectural approach that breaks large applications into smaller, independently deployable services.

Containerization complements microservices by providing isolation, portability, and consistency across environments.

This phase focused on conceptual clarity rather than implementation depth.

