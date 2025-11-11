# Go Web DevOps – End-to-End Cloud-Native Demo

This project is a simple Go web application that I used to practice and implement a complete DevOps workflow — from writing the application, to containerizing it, deploying it on Kubernetes, and automating everything with CI/CD and GitOps.

The goal of this project wasn’t to build a complex product, but to understand how real-world DevOps pipelines come together when working with cloud resources, container orchestration, and automated deployments.

---

## 🚀 What This Project Demonstrates

### ✅ Multi-Stage Docker Build
The application is packaged using a multi-stage Dockerfile, keeping the final image lean and production-friendly.

### ✅ Kubernetes Manifests + Helm Chart
The app is deployed on Kubernetes using both:
- **raw manifests** (for understanding the basics)
- **a Helm chart** (for managing multiple environments cleanly)

### ✅ CI Pipeline – GitHub Actions
A GitHub Actions workflow handles:
- building the Go binary  
- running tests  
- linting with golangci-lint  
- building & pushing the Docker image to DockerHub  

Every push to `master` automatically triggers the pipeline.

### ✅ CD with Argo CD (GitOps)
Argo CD watches this repository and automatically syncs deployments to the Kubernetes cluster whenever the Helm chart gets a new tag.

### ✅ Kubernetes Ingress + DNS
The application is exposed through an Ingress controller using an AWS Load Balancer.  
Custom DNS routing can be added for cleaner access.

---

## 🛠️ Tech Stack

**Languages & Frameworks**
- Go (Golang)

**DevOps / Cloud**
- Docker & Multi-Stage Builds  
- Kubernetes (EKS)  
- Helm  
- GitHub Actions  
- Argo CD (GitOps CD)  
- AWS Load Balancer + Route 53 (optional)

---

## 📦 Running Locally

You can run this app locally with:

```bash
go run main.go
```

## 🔄 CI/CD Workflow Overview

- Commit pushed → GitHub Actions builds, tests, and pushes the Docker image

- The workflow updates the image tag inside the Helm chart

- Argo CD detects the change and syncs it to the Kubernetes cluster

- The app rolls out with the new version automatically

- This replicates how modern GitOps pipelines work in production teams.

<img width="720" height="1065" alt="Go-DevOpsify" src="https://github.com/user-attachments/assets/a7804b27-ada6-4269-9d27-5c9e0305881c" />

