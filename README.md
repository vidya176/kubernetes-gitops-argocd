# Kubernetes GitOps Deployment using Kops, Helm & Argo CD

## 📌 Project Overview

This project demonstrates the implementation of a GitOps-based Continuous Delivery workflow using Kubernetes, Kops, Helm, and Argo CD on AWS.

The Kubernetes cluster is provisioned using Kops, Argo CD is installed using Helm, and applications are deployed automatically from a GitHub repository. Any changes pushed to GitHub are synchronized with the Kubernetes cluster through Argo CD, enabling automated and declarative application delivery.

---

## 🚀 Project Objectives

- Provision a Kubernetes cluster using Kops
- Install and configure Helm
- Deploy Argo CD using Helm
- Expose the Argo CD server through a LoadBalancer
- Deploy Kubernetes applications using GitOps principles
- Enable automatic synchronization between GitHub and Kubernetes

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Git & GitHub | Source Code Management |
| Kubernetes | Container Orchestration |
| Kops | Kubernetes Cluster Provisioning |
| AWS | Cloud Infrastructure |
| Helm | Kubernetes Package Manager |
| Argo CD | GitOps Continuous Delivery |
| kubectl | Kubernetes CLI |
| Linux (Amazon Linux) | Operating System |

---

## 🏗️ Infrastructure Setup

| Server | Purpose |
|---------|---------|
| Kops Server | Cluster Provisioning |
| AWS EC2 Instances | Kubernetes Control Plane & Worker Nodes |
| S3 Bucket | Kops State Store |
| GitHub Repository | Kubernetes Manifests |
| Argo CD | GitOps Deployment Tool |

---

## 🔄 GitOps Workflow

1. Provision Kubernetes Cluster using Kops.
2. Install Helm.
3. Deploy Argo CD.
4. Expose Argo CD Server using a LoadBalancer.
5. Connect Argo CD to the GitHub repository.
6. Configure an Application in Argo CD.
7. Synchronize Kubernetes manifests.
8. Deploy the application automatically to the Kubernetes cluster.

---

## ⚙️ Components Used

- Kubernetes Cluster
- Kops
- Helm
- Argo CD
- AWS EC2
- Amazon S3
- kubectl

---

## 📂 Repository Structure

```
kubernetes-gitops-argocd
│
├── README.md
├── .gitignore
├── LICENSE
│
├── manifests/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── namespace.yaml
│
├── scripts/
│   ├── kops.sh
│   └── helm-install.sh
│
├── docs/
│   └── setup-guide.md
│
└── images/
    ├── architecture.png
    ├── cluster.png
    ├── argocd-dashboard.png
    ├── sync-status.png
    └── application-running.png
```

---

## ✨ Key Features

- Kubernetes Cluster Provisioning
- GitOps Deployment
- Continuous Delivery
- Declarative Infrastructure
- Automated Synchronization
- Helm-based Installation
- LoadBalancer Exposure
- AWS Cloud Deployment
- Version-controlled Infrastructure

---

## 📁 Project Files

| File | Description |
|------|-------------|
| deployment.yaml | Kubernetes Deployment |
| service.yaml | Kubernetes Service |
| namespace.yaml | Namespace Definition |
| kops.sh | Cluster Provisioning Script |
| helm-install.sh | Helm Installation Script |

---

## 📸 Screenshots

- Kops Cluster
- kubectl get nodes
- Helm Installation
- Argo CD Dashboard
- Application Details
- Sync Status
- Kubernetes Pods
- Kubernetes Services
- Running Application

---

## 📚 Skills Demonstrated

- Kubernetes
- Kops
- Helm
- Argo CD
- GitOps
- AWS
- Linux
- Git & GitHub
- kubectl
- Continuous Delivery

---

## 🔮 Future Enhancements

- Deploy using EKS
- Add Prometheus & Grafana Monitoring
- Integrate Jenkins CI
- Use Terraform for Infrastructure
- Configure Argo Rollouts
- Add RBAC & Security Policies

---

