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

3. **Run teh cluster setup script**:
   ```bash
   ./scripts/setup-cluster.sh
  This will initiate the Kubeadm process to install Kubernetes, set up the control plane, and add the worker nodes.

4. **Install ContainerD**:
  ```bash
   ./scripts/install-containerd.sh
