A demonstration of Docker to implement a simple 3 tier architecture

* frontend will be able to access the mid-tier
* mid-tier will be able to access the db

In order to run this in docker, simply type ```docker-compose up``` at the command prompt. Docker will then create the [MongoDB](https://www.mongodb.com/) from the stock [mongo](https://hub.docker.com/_/mongo) image. The api uses [nodejs](https://nodejs.org/) with [express](http://expressjs.com/) and is built from a [node:alpine](https://hub.docker.com/_/node) image. The front end uses [ReactJS](https://reactjs.org/) and built from a [node:alpine](https://hub.docker.com/_/node) image.

# 🚀 DevOps Engineer Task – 3-Tier Application Deployment

## 📌 Project Overview

This project demonstrates scalable and production-grade DevOps practices by deploying a 3-tier application (frontend + backend + database) on **Azure Kubernetes Service (AKS)**. It includes:

- Infrastructure provisioning using **Terraform**
- Kubernetes orchestration via **Helm**
- CI/CD automation using **GitHub Actions**
- Monitoring with **Prometheus** and **Grafana**
- Docker image hosting on **Docker Hub**

---

## 🛠️ Tech Stack

| Layer             | Tool/Technology              |
|------------------|------------------------------|
| Cloud Platform   | Azure (AKS)                  |
| IaC              | Terraform                    |
| Containerization | Docker                       |
| Orchestration    | Kubernetes + Helm            |
| CI/CD            | GitHub Actions               |
| Registry         | Docker Hub                   |
| Monitoring       | Prometheus + Grafana         |

---

## 📁 Project Structure

```bash
.
├── terraform/                 # Infrastructure as Code (AKS, networking)
├── helm/                     # Helm charts (backend, frontend)
│   ├── backend/
│   └── frontend/
├── docker/                   # Dockerfiles for services
├── .github/
│   └── workflows/            # GitHub Actions CI/CD pipelines
├── monitoring/               # Prometheus and Grafana Helm config
├── manifests/                # Optional raw K8s manifests
├── README.md
🔧 Infrastructure Provisioning (Terraform)
Provisioning includes:

Azure Resource Group

AKS Cluster

Networking components

Usage
bash
Copy
Edit
cd terraform
terraform init
terraform plan
terraform apply
🐳 Docker Image Management
Docker images for frontend and backend are built and pushed to Docker Hub.

Dockerfiles are available in the docker/ directory.

Example
bash
Copy
Edit
docker build -t yourdockerhubuser/backend:latest ./docker/backend
docker push yourdockerhubuser/backend:latest
☸️ Kubernetes with Helm
Helm is used to package and deploy services into the AKS cluster.

Services include Deployments, Services, and Ingress (if applicable).

Helm Commands
bash
Copy
Edit
helm install backend ./helm/backend
helm install frontend ./helm/frontend
🔁 CI/CD via GitHub Actions
CI: Triggered on push, runs linting, builds Docker images, pushes to Docker Hub

CD: Deploys to AKS using Helm on main branch merges

Workflows are stored in .github/workflows/.

📊 Monitoring (Prometheus + Grafana)
Deployed using Helm charts:

bash
Copy
Edit
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm install prometheus prometheus-community/kube-prometheus-stack
Access Dashboards
bash
Copy
Edit
kubectl get svc -n monitoring
Grafana default credentials:

User: admin

Password: admin

🎯 Bonus Features Implemented
✅ Auto-deploy on merge to main
✅ CI/CD separation for backend & frontend
✅ Prometheus and Grafana dashboards
✅ Docker Hub image hosting
✅ Secrets managed via Kubernetes Secrets

📷 Architecture Diagram

<!-- Replace or rename if you have the diagram file -->
📽 Video Walkthrough
🎥 Loom Walkthrough: Watch Here

This video walks through the infrastructure, CI/CD pipeline, deployments, and monitoring dashboards.

💬 Contact
If you have any questions, feel free to reach out to me at [your-email@example.com].
