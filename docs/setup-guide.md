# Kubernetes GitOps Deployment using Kops & Argo CD

## Overview

This project demonstrates a GitOps-based Continuous Delivery workflow using Kubernetes, Kops, Helm, and Argo CD on AWS.

The Kubernetes cluster is provisioned using Kops, Argo CD is installed with Helm, and applications are deployed from a GitHub repository. Any changes pushed to the repository can be synchronized to the Kubernetes cluster through Argo CD.

---

# Architecture

```
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Argo CD
    │
    ▼
Kubernetes Cluster (Created using Kops)
    │
    ▼
Application Pods
    │
    ▼
LoadBalancer Service
    │
    ▼
End Users
```

---

# Prerequisites

- AWS Account
- IAM User with Administrator Access
- AWS CLI Configured
- Amazon Linux 2 EC2 Instance
- kubectl Installed
- Kops Installed
- Helm Installed
- S3 Bucket for Kops State Store

---

# Infrastructure

| Resource | Purpose |
|----------|---------|
| EC2 Instance | Kops Management Server |
| S3 Bucket | Kops State Store |
| AWS IAM User | Cluster Provisioning Permissions |
| Kubernetes Cluster | Container Orchestration |
| Argo CD | GitOps Continuous Delivery |

---

# Step 1 – Configure AWS Access

Create an IAM user with **AdministratorAccess**.

Generate:

- Access Key
- Secret Access Key

Configure AWS CLI.

```bash
aws configure
```

Verify access.

```bash
aws sts get-caller-identity
```

---

# Step 2 – Install Kops

Download and install Kops.

Verify installation.

```bash
kops version
```

Create an S3 bucket and export the state store.

```bash
export KOPS_STATE_STORE=s3://<your-kops-state-store>
```

---

# Step 3 – Create Kubernetes Cluster

Create the Kubernetes cluster using Kops.

```bash
kops create cluster
```

Apply the configuration.

```bash
kops update cluster --yes
```

Validate the cluster.

```bash
kops validate cluster
```

Verify nodes.

```bash
kubectl get nodes
```

---

# Step 4 – Install Helm

Download and install Helm.

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3

chmod 700 get_helm.sh

./get_helm.sh
```

Verify installation.

```bash
helm version
```

---

# Step 5 – Install Argo CD

Add the Argo CD Helm repository.

```bash
helm repo add argo-cd https://argoproj.github.io/argo-helm

helm repo update
```

Create the namespace.

```bash
kubectl create namespace argocd
```

Install Argo CD.

```bash
helm install argocd argo-cd/argo-cd -n argocd
```

Verify the installation.

```bash
kubectl get all -n argocd
```

---

# Step 6 – Expose Argo CD

Expose the Argo CD server using a LoadBalancer.

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec":{"type":"LoadBalancer"}}'
```

Verify the service.

```bash
kubectl get svc -n argocd
```

Open the LoadBalancer URL in your browser.

---

# Step 7 – Retrieve the Argo CD Password

Retrieve the initial admin password.

```bash
kubectl -n argocd get secret argocd-initial-admin-secret \
-o jsonpath="{.data.password}" | base64 -d
```

Login with:

- **Username:** 
- **Password:** 

---

# Step 8 – Deploy an Application

In the Argo CD dashboard:

1. Click **New App**
2. Enter the application name
3. Select the **default** project
4. Choose **Manual** or **Automatic** sync
5. Enter the GitHub repository URL
6. Set the repository path
7. Select the target Kubernetes cluster
8. Choose the target namespace
9. Click **Create**

If Manual Sync is selected:

- Click **Sync**
- Click **Synchronize**

---

# Step 9 – Verify Deployment

Check Kubernetes resources.

```bash
kubectl get pods

kubectl get svc

kubectl get deployments
```

Open the application using the LoadBalancer service URL.

---

# Repository Structure

```
kubernetes-gitops-argocd/
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
```

---

# Skills Demonstrated

- Kubernetes
- Kops
- Helm
- Argo CD
- GitOps
- AWS
- kubectl
- Linux Administration
- Continuous Delivery
- Infrastructure Automation

---

# Future Enhancements

- Deploy on Amazon EKS
- Integrate Jenkins CI
- Add Prometheus & Grafana Monitoring
- Configure Argo Rollouts
- Implement RBAC Policies
- Provision Infrastructure using Terraform

---


