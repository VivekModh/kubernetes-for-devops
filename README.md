Kubernetes for DevOps 🚀

A personal repository for learning and experimenting with Kubernetes locally using Kind.

This repository serves as my personal lab for mastering Kubernetes concepts as part of my DevOps journey. It contains the necessary scripts to set up a local cluster, Kubernetes manifests to deploy sample applications, and a cheatsheet of common commands.

📂 Repository Structure
kubernetes-for-devops/
├── config.yml          # Configuration file for the Kind cluster
├── install.sh          # Installation script for all dependencies
├── nginx/              # Namespace for learning Networking
├── mysql/              # Namespace for learning Storage
└── apache/             # Namespace for learning Scaling & Scheduling

⚙️ Getting Started
Prerequisites

A Linux-based environment (or WSL2 on Windows)

git for cloning the repository

sudo privileges for installing software

Installation
# Clone this repository
git clone https://github.com/VivekModh/kubernetes-for-devops.git
cd kubernetes-for-devops

# Make the installation script executable
chmod +x install.sh

# Run the script to install Docker, Kind, and kubectl
./install.sh

# Create your local Kind cluster
kind create cluster --name=vivekmodh-cluster --config=config.yml


Your local Kubernetes lab is now ready!

🖥️ Usage & Common Commands Cheatsheet
✅ Verify Installations
docker --version
kind --version
kubectl version

☸️ Kind Cluster Management
# List all Kind clusters
kind get clusters

# Delete a specific cluster
kind delete cluster --name vivekmodh-cluster

🔎 Cluster Inspection
kubectl cluster-info
kubectl get nodes

🗂️ Namespaces and Topics
🌐 Networking in nginx namespace

Basic Pod-to-Pod communication

Cluster Networking fundamentals

Services (ClusterIP, NodePort, LoadBalancer)

Ingress for external access

Network Policies for access control

💾 Storage in mysql namespace

Persistent Volumes (PV)

Persistent Volume Claims (PVC)

StorageClasses for dynamic provisioning

ConfigMaps for configuration management

⚖️ Scaling & Scheduling in apache namespace

Horizontal Pod Autoscaler (HPA)

Vertical Pod Autoscaler (VPA)

Node Affinity & Anti-Affinity

Taints and Tolerations

Resource Quotas & Limits

Liveness & Readiness Probes

📦 Managing Resources
Declarative Approach (preferred)
# Apply all manifests in a namespace directory
kubectl apply -f nginx/
kubectl apply -f mysql/
kubectl apply -f apache/

Imperative Approach (quick tests)
kubectl run nginx-pod --image=nginx -n nginx
kubectl delete pod nginx-pod -n nginx

💻 Debugging & Logs
kubectl exec -it <pod-name> -n <namespace> -- bash
kubectl logs <pod-name> -n <namespace>

🛑 Troubleshooting

If you face conflicts with ports (80/443):

sudo lsof -i :80
sudo systemctl stop apache2
sudo systemctl disable apache2


For Load generator this command i used
kubectl run -i --tty load-generator --image=busybox -n apache /bin/sh
