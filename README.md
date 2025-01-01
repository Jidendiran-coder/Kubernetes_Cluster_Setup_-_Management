

### Project: **Kubernetes Cluster Setup and Management**

---

### Project Directory Structure:
```plaintext
├── .github/                   # GitHub Actions (CI/CD) workflows
│   └── workflows/
├── manifests/                  # Kubernetes deployment manifests
│   ├── app-deployment.yaml
│   ├── app-service.yaml
│   ├── ingress.yaml
│   └── k8s-setup/
│       ├── calico-config.yaml
│       ├── k8s-nodeport.yaml
│       └── k8s-loadbalancer.yaml
├── docs/                       # Documentation files
│   ├── cluster-setup.md
│   └── knowledge-transfer.md
├── scripts/                    # Setup & deployment scripts
│   ├── setup-cluster.sh
│   ├── install-containerd.sh
│   └── deploy-app.sh
├── Dockerfile                  # If you need to deploy your app container
├── README.md                   # Project description & setup instructions
└── LICENSE                     # Licensing information
```

---

# Kubernetes Cluster Setup and Management

This repository demonstrates the end-to-end process of setting up a resilient three-node Kubernetes cluster using Kubeadm. The setup includes high availability with one control plane node and two data plane nodes. The project also integrates ContainerD as the container runtime and utilizes Calico as the network plugin for secure, scalable communication.

## Project Features

- **Kubernetes Cluster Setup**: A high-availability three-node setup with Kubeadm.
- **Container Runtime**: Use of ContainerD to optimize container efficiency.
- **Networking**: Calico as the Container Network Interface (CNI) for network policies and secure communication.
- **Service Exposure**: Configured NodePort for exposing services externally and LoadBalancer with Kemp Ingress Controller.
- **Deployment**: Kubernetes manifests for application deployment, along with Helm charts for scalable infrastructure management.
- **CI/CD**: GitHub Actions for continuous integration and continuous deployment.
- **Documentation**: Detailed knowledge transfer documentation for IT teams.

## Table of Contents

- [Installation](#installation)
- [Setup Guide](#setup-guide)
- [Deployment Guide](#deployment-guide)
- [CI/CD Pipeline](#cicd-pipeline)
- [Knowledge Transfer](#knowledge-transfer)
- [License](#license)

## Installation

1. **Prerequisites**
   - A minimum of three machines or VMs.
   - Each machine must have a Linux-based OS (Ubuntu preferred).
   - Kubernetes version: 1.24+
   - ContainerD as the container runtime.

2. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/kubernetes-cluster-setup.git
   cd kubernetes-cluster-setup

3. **Run the cluster setup script**:
   ```bash
   ./scripts/setup-cluster.sh
   ```

   This will initiate the Kubeadm process to install Kubernetes, set up the control plane, and add the worker nodes.

4. **Install ContainerD**:
   ```bash
   ./scripts/install-containerd.sh
   ```

   Ensure ContainerD is installed and running on all nodes.

## Setup Guide

1. **Initialize the control plane**:
   Follow the instructions to initialize the control plane node using `kubeadm init`:

   ```bash
   kubeadm init --pod-network-cidr=192.168.0.0/16
   ```

2. **Join the worker nodes**:
   Once the control plane is set up, join the worker nodes using the `kubeadm join` command provided after the `kubeadm init`.

3. **Install Calico CNI**:
   Set up Calico networking by applying the CNI configuration from `manifests/k8s-setup/calico-config.yaml`:
   ```bash
   kubectl apply -f manifests/k8s-setup/calico-config.yaml
   ```

4. **Expose Services**:
   Configure the NodePort and LoadBalancer using the manifests in `manifests/k8s-setup/`:
   ```bash
   kubectl apply -f manifests/k8s-setup/k8s-nodeport.yaml
   kubectl apply -f manifests/k8s-setup/k8s-loadbalancer.yaml
   ```

5. **Deploy Applications**:
   Deploy your application using the following Kubernetes manifests for your app in `manifests/app-deployment.yaml`:
   ```bash
   kubectl apply -f manifests/app-deployment.yaml
   kubectl apply -f manifests/app-service.yaml
   kubectl apply -f manifests/ingress.yaml
   ```

## Deployment Guide

- **Apps Deployment**:
  Use the `deploy-app.sh` script to deploy your app across all nodes.
  ```bash
  ./scripts/deploy-app.sh
  ```

## CI/CD Pipeline

- **GitHub Actions**: We’ve integrated a simple CI/CD pipeline with GitHub Actions to automate testing and deployment.

  The pipeline can be found in `.github/workflows/ci-cd.yml`, which includes:
  - Linting and testing for Kubernetes manifests.
  - Application deployment using Helm.

## Knowledge Transfer

A comprehensive knowledge transfer document is available for IT teams to understand the cluster setup and deployment processes.

- [Cluster Setup Guide](docs/cluster-setup.md)
- [Knowledge Transfer Document](docs/knowledge-transfer.md)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```

---

### **Key Points for Each Section**

1. **Setup Scripts** (`scripts/`):
   - **setup-cluster.sh**: Automates the process of setting up the Kubernetes cluster, installing required components, and configuring the control plane.
   - **install-containerd.sh**: Script to install ContainerD, which is the chosen container runtime.
   - **deploy-app.sh**: Used for deploying applications to the cluster, ensuring repeatable deployments.

2. **Kubernetes Manifests** (`manifests/`):
   - Includes YAML files for deploying applications, services, ingress, and network configurations.
   - Example configurations for Calico, LoadBalancer, and NodePort setup.

3. **Documentation** (`docs/`):
   - **Cluster Setup Guide**: Detailed guide to help others set up the cluster.
   - **Knowledge Transfer Document**: Contains a walkthrough for IT teams on managing and scaling the infrastructure.

---

This structure provides clear documentation and a professional approach that will help demonstrate your experience with Kubernetes, containerization, and modern cloud architectures on GitHub.
4. **Install ContainerD**:
  ```bash
   ./scripts/install-containerd.sh


