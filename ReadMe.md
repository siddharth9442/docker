# Docker Learning Repository
This repository contains my Docker learning journey, including theory, concepts, and hands-on projects built using Docker.

## Topics Covered

### 1. What is Docker?

Docker is a containerization platform that allows developers to package applications along with their dependencies into lightweight and portable containers.

### Benefits of Docker

* Consistent development and production environments
* Easy application deployment
* Faster setup and onboarding
* Better resource utilization compared to virtual machines
* Simplified dependency management

---

### 2. Docker Images

A Docker Image is a read-only template used to create containers.

Docker Image is a standardized package that includes:
* all of the files
* binaries
* libraries
* configurations

In short we can say that, 'A Docker Image is a blueprint or template required for creating a container'.

Examples:

```bash
docker pull node
docker pull python
docker images
```

Key Points:

* Images are built using a Dockerfile.
* Images contain application code, runtime, libraries, and dependencies.
* Images are immutable.

---

### 3. Docker Containers

A container is a running instance of a Docker image.

Examples:

```bash
docker run nginx
docker ps
docker stop <container-id>
```

Key Points:

* Self contained
* Lightweight and isolated.
* Can be started, stopped, and removed easily.
* Multiple containers can run from the same image.
* Can be managed independently.
* Portable

---

### 4. Dockerfile

A Dockerfile contains instructions for building a Docker image.

Example:

```dockerfile
FROM node:slim

WORKDIR /app

COPY . /app

RUN npm install

EXPOSE 3000

CMD ["node", "index.js"]
```

Common Instructions:

| Instruction | Purpose                       |
| ----------- | ----------------------------- |
| FROM        | Base image                    |
| WORKDIR     | Working directory             |
| COPY        | Copy files                    |
| RUN         | Execute commands during build |
| EXPOSE      | Document container port       |
| CMD         | Default command to run        |

---

### 5. Docker Networking

Docker provides networking between containers.

Types of Networks:

* Bridge Network
* Host Network
* None Network
* Custom Networks

Example:

```bash
docker network create my-network
```

Containers on the same network can communicate using container names.

---

### 6. Docker Volumes

Volumes provide persistent storage for containers.

Example:

```bash
docker volume create mongo-data
```

Mount Volume:

```bash
docker run -v mongo-data:/data/db mongo
```

Benefits:

* Data persists after container deletion.
* Easy backup and migration.
* Recommended for databases.

---

### 7. Docker Compose

Docker Compose helps manage multiple containers using a single YAML file.

Example:

```yaml
services:
  app:
    build: .

  mongo:
    image: mongo
```

Commands:

```bash
docker compose up
docker compose down
```

Benefits:

* Multi-container management
* Easier configuration
* Reproducible environments

---

### Data Persistence

Data persistence ensures that application data remains available even after a container is stopped, removed, recreated or deleted.

In Docker, data persistence is commonly achieved using:

- Named Volumes
- Bind Mounts

Benefits:

- Prevents data loss when containers are deleted
- Suitable for databases and application storage
- Allows data sharing between containers
- Separates application lifecycle from data lifecycle

Example:

```bash
docker run -d \
  --name mongodb \
  -v mongo-data:/data/db \
  mongo
  ```

## Projects

### 1. Node.js Application

A simple Node.js application containerized using Docker.

Features:

* Custom Dockerfile
* Port Mapping
* Docker Image Creation
* Docker Container Execution

Run:

```bash
docker build -t node-app .
docker run -p 3000:3000 node-app
```

---

### 2. Python Flask Application

A simple Flask application containerized using Docker.

Features:

* Python Base Image
* Dependency Installation using requirements.txt
* Containerized Flask Server

Run:

```bash
docker build -t flask-app .
docker run -p 3000:3000 flask-app
```

---

## Repository Structure

```text
docker/
│
├── node-app/
│   ├── Dockerfile
│   └── source code
│
├── flask-app/
│   ├── Dockerfile
│   └── source code
│
└── README.md
```

---

## Learning Outcomes

Through this repository, I learned:

* Docker fundamentals
* Images and Containers
* Dockerfile creation
* Port Mapping
* Volumes
* Networking
* Docker Compose
* Data Persistence
* Building and running containerized applications
* Containerizing Node.js applications
* Containerizing Python Flask applications

---

<!-- ## Future Plans

* MongoDB with Docker
* MongoDB + Mongo Express using Docker Compose
* Multi-container applications
* Custom Networks
* Nginx Reverse Proxy
* Docker Swarm
* Kubernetes Basics
* CI/CD Integration with Docker -->