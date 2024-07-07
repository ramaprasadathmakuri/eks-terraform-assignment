# Kubernetes on AWS with Terraform and EKS

## Prerequisites

- AWS CLI
- Terraform
- kubectl
- eksctl
- Helm

## Project Directory Structure


## Steps to Set Up

### 1. Terraform Configuration

1. **Navigate to the `terraform` directory:**

    ```bash
    cd terraform
    ```

2. **Initialize and apply the Terraform scripts:**

    ```bash
    terraform init
    terraform apply -auto-approve
    ```

### 2. Generate Kubeconfig

1. **Make the script executable:**

    ```bash
    chmod +x generate_kubeconfig.sh
    ```

2. **Run the script to generate the kubeconfig file:**

    ```bash
    ./generate_kubeconfig.sh
    ```

    The kubeconfig file will be generated and saved to `~/.kube/config`.

### 3. Eksctl Configuration

1. **Create an EKS cluster:**

    ```bash
    eksctl create cluster -f eksctl/eks-cluster.yaml
    ```

### 4. Kubernetes Configuration

1. **Deploy the NGINX application:**

    ```bash
    kubectl apply -f ../kubernetes/nginx-deployment.yaml
    ```

2. **Set up RBAC:**

    ```bash
    kubectl apply -f ../kubernetes/rbac.yaml
    ```

### 5. Deploy K8s Canary App

1. **Navigate to the canary app directory:**

    ```bash
    cd ../kubernetes/canary-app
    ```

2. **Deploy the Canary app using Helm:**

    ```bash
    helm install canary ./helm-canary
    ```

### 6. Verification

1. **Verify the deployments and services:**

    ```bash
    kubectl get deployments
    kubectl get services
    ```

### 7. Destroy the Canary App

1. **Uninstall the Canary app using Helm:**

    ```bash
    helm uninstall canary
    ```

