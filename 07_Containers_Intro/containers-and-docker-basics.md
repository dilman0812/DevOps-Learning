# Containers & Docker – Overview + Basic Hands-On

---

# 1. What is a Container?

A container is a lightweight, isolated runtime environment that packages:

- Application code
- Runtime
- System libraries
- Dependencies
- Configuration

Containers use **OS-level virtualization** and share the host operating system kernel, making them significantly more lightweight than traditional virtual machines.

---

# 2. Why Containers Matter

Containers enable:

- Environment consistency (Development → Testing → Production)
- Faster deployments
- Lightweight resource usage
- Portability across infrastructure
- Foundation for cloud-native applications

Containers eliminate the classic:
"It works on my machine" problem.

---

# 3. What is Docker?

Docker is an open platform for developing, shipping, and running applications inside containers.

It allows developers to:

- Standardize environments
- Package applications with dependencies
- Simplify deployments
- Improve CI/CD workflows

Docker follows a **client-server architecture**.

Main components:

- Docker Client (`docker`)
- Docker Daemon (`dockerd`)
- Docker Registry (Docker Hub by default)

---

# 4. Docker Architecture (High-Level)

Docker works using a client-server model:

- The **Docker Client** sends commands.
- The **Docker Daemon** builds and runs containers.
- **Images** are stored in registries.
- **Containers** are created from images.

Basic lifecycle:

Dockerfile → Build → Image → Run → Container

---

# 5. Hands-On: Installing Docker Engine on VM

## Environment Setup

- Installed **Docker Engine** on a Virtual Machine.
- Verified installation using:

```bash
docker --version
```

---

# 6. Running the First Container

Ran the official test container:

```bash
docker run hello-world
```

### What Happened Internally:

1. Docker checked if the `hello-world` image existed locally.
2. If not found, Docker pulled it from Docker Hub.
3. Docker created a new container.
4. The container executed.
5. A confirmation message was displayed.

This verified:

- Docker installation
- Image pulling
- Container creation
- Container execution

---

# 7. Basic Docker Commands Practiced

## List Images

```bash
docker images
```

## List Running Containers

```bash
docker ps
```

## List All Containers (Including Stopped)

```bash
docker ps -a
```

## Remove an Image

```bash
docker rmi <image_id>
```

## Remove a Container

```bash
docker rm <container_id>
```

---

# 8. Images vs Containers

Image:
- Read-only template
- Blueprint for containers
- Built in layers

Container:
- Runnable instance of an image
- Has a writable layer
- Ephemeral by default (unless data is persisted)

---

# 9. Scope of This Learning Phase

Covered:

- Container fundamentals
- Docker overview
- Docker architecture basics
- Installing Docker Engine on a VM
- Running `hello-world`
- Basic CLI commands
- Understanding images vs containers

Not covered yet (to be explored later):

- Writing Dockerfiles
- Volumes and persistent storage
- Networking
- Docker Compose
- Multi-container applications
- Production-level containerization

