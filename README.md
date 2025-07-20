# 🚀 DevOps Engineer Task – 3-Tier Application Deployment

A demonstration of Docker to implement a simple 3-tier architecture where the frontend can access the mid-tier and the mid-tier can access the database.

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
| **Cloud Platform**   | Azure (AKS)                  |
| **IaC**              | Terraform                    |
| **Containerization** | Docker                       |
| **Orchestration**    | Kubernetes + Helm            |
| **CI/CD**            | GitHub Actions               |
| **Registry**         | Docker Hub                   |
| **Monitoring**       | Prometheus + Grafana         |
| **Database**         | MongoDB                      |
| **Backend**          | Node.js + Express            |
| **Frontend**         | ReactJS                      |

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
├── docker-compose.yml        # Local development setup
└── README.md
```

---

## 🏃‍♂️ Quick Start

### Local Development
For local development, simply run:
```bash
docker-compose up
```

Docker will create the services using:
- **Database**: [MongoDB](https://www.mongodb.com/) from the stock [mongo](https://hub.docker.com/_/mongo) image
- **Backend**: [Node.js](https://nodejs.org/) with [Express](http://expressjs.com/) built from [node:alpine](https://hub.docker.com/_/node) image
- **Frontend**: [ReactJS](https://reactjs.org/) built from [node:alpine](https://hub.docker.com/_/node) image

---

## 🔧 Infrastructure Provisioning (Terraform)

Provisioning includes:
- Azure Resource Group
- AKS Cluster
- Networking components

### Usage
```bash
cd terraform
terraform init
terraform plan
terraform apply
```

---

## 🐳 Docker Image Management

Docker images for frontend and backend are built and pushed to Docker Hub.

Dockerfiles are available in the `docker/` directory.

```bash
# Build and push backend image
docker build -t yourdockerhubuser/backend:latest ./docker/backend
docker push yourdockerhubuser/backend:latest

# Build and push frontend image
docker build -t yourdockerhubuser/frontend:latest ./docker/frontend
docker push yourdockerhubuser/frontend:latest
```

---

## ☸️ Kubernetes with Helm

Helm is used to package and deploy services into the AKS cluster.
Services include Deployments, Services, and Ingress (if applicable).

### Helm Commands

```bash
# Deploy backend
helm install backend ./helm/backend

# Deploy frontend
helm install frontend ./helm/frontend

# Upgrade deployments
helm upgrade backend ./helm/backend
helm upgrade frontend ./helm/frontend
```

---

## 🔁 CI/CD via GitHub Actions

- **CI**: Triggered on push, runs linting, builds Docker images, pushes to Docker Hub
- **CD**: Deploys to AKS using Helm on main branch merges

Workflows are stored in `.github/workflows/`.

### Pipeline Features
- ✅ Auto-deploy on merge to main
- ✅ CI/CD separation for backend & frontend
- ✅ Docker Hub image hosting
- ✅ Secrets managed via Kubernetes Secrets

---

## 📊 Monitoring (Prometheus + Grafana)

Deployed using Helm charts:

```bash
# Add Helm repositories
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts

# Install monitoring stack
helm install prometheus prometheus-community/kube-prometheus-stack
```

### Access Dashboards

```bash
kubectl get svc -n monitoring
```

**Grafana default credentials:**
- User: `admin`
- Password: `admin`

---

## 🎯 Bonus Features Implemented

✅ Auto-deploy on merge to main  
✅ CI/CD separation for backend & frontend  
✅ Prometheus and Grafana dashboards  
✅ Docker Hub image hosting  
✅ Secrets managed via Kubernetes Secrets  

---

## 📷 Architecture Diagram

![Architecture Diagram](https://github.com/mdriyazali/3-tier-application/blob/main/Architecture%20diagram.jpg)

*3-tier architecture deployed on Azure Kubernetes Service with complete DevOps pipeline*

---

## 📽️ Video Walkthrough

🎥 **Project Demonstration**: [Watch Here](https://drive.google.com/file/d/1--bODMQ11Nd0Q2WN_v_cBI-xm0SGSwoI/view?usp=sharing)

This video walks through the infrastructure, CI/CD pipeline, deployments, and monitoring dashboards.

---

## 🚦 Getting Started

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd <repo-name>
   ```

2. **Set up Azure credentials**
   ```bash
   az login
   az account set --subscription <your-subscription-id>
   ```

3. **Deploy infrastructure**
   ```bash
   cd terraform
   terraform init && terraform apply
   ```

4. **Configure kubectl**
   ```bash
   az aks get-credentials --resource-group <rg-name> --name <aks-name>
   ```

5. **Deploy applications**
   ```bash
   helm install backend ./helm/backend
   helm install frontend ./helm/frontend
   ```

---

## 🔐 Environment Variables

Create the following secrets in your Kubernetes cluster:

```bash
kubectl create secret generic app-secrets \
  --from-literal=MONGODB_URI=<your-mongodb-uri> \
  --from-literal=API_KEY=<your-api-key>
```

---

## 🧪 Testing

```bash
# Check pod status
kubectl get pods

# Check services
kubectl get svc

# View logs
kubectl logs -f deployment/backend
kubectl logs -f deployment/frontend
```

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 💬 Contact

If you have any questions, feel free to reach out to me at **mdriyazali254362@gmail.com**

---

## 🙏 Acknowledgments

- Azure Kubernetes Service documentation
- Helm community charts
- Docker Hub for container registry
- GitHub Actions for CI/CD automation
- Prometheus and Grafana communities for monitoring solutions
