# Train Schedule Application – CI/CD with Docker Compose

This project demonstrates a containerized application deployment using Jenkins CI/CD and Docker Compose on a single EC2 instance.

---

## 🏗 Architecture Overview

Developer

    ↓

GitHub

    ↓ (Webhook)

Jenkins CI Server

    ↓

Docker Build (v${BUILD_NUMBER})
 
    ↓

Push to DockerHub
 
    ↓

SSH Deployment to EC2

    ↓

docker compose pull

docker compose up -d

---

## ⚙️ Deployment Strategy

Each code push triggers:

1. Jenkins builds Docker image using version tag `v${BUILD_NUMBER}`
2. Image pushed to DockerHub
3. Jenkins connects to EC2 via SSH
4. Docker Compose pulls updated image
5. Containers are recreated using:

docker compose pull
docker compose up -d


This ensures controlled and repeatable deployments.

---

## 🐳 Container Orchestration

Docker Compose manages:

- Application container
- (Optional) Nginx reverse proxy
- Internal Docker bridge networking
- Service-level DNS resolution

Compose acts as a lightweight single-node orchestrator.

---

## 🔐 Security Considerations

- Key-based SSH authentication
- Credentials stored securely in Jenkins
- Controlled inbound security group rules

---

## 🎯 Key Concepts Demonstrated

- CI/CD automation
- Immutable Docker image versioning
- SSH-based deployment
- Docker Compose orchestration
- Single-node containerized runtime
