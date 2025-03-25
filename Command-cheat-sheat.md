# Kubernetes (CKA) Exam Command Cheat Sheet

## Cluster Management
```bash
# View cluster information
kubectl cluster-info
kubectl config view
kubectl config current-context

# List nodes
kubectl get nodes
kubectl describe nodes <node-name>

# Check cluster component status
kubectl get componentstatuses
```

## Namespace Operations
```bash
# List namespaces
kubectl get namespaces
kubectl get ns

# Create namespace
kubectl create namespace <namespace-name>
kubectl create ns <namespace-name>

# Set default namespace
kubectl config set-context --current --namespace=<namespace-name>
```

## Pod Management
```bash
# Create pod
kubectl run <pod-name> --image=<image-name>
kubectl apply -f pod.yaml

# List pods
kubectl get pods
kubectl get pods -A  # All namespaces
kubectl get pods -o wide  # Detailed view
kubectl get pods -n <namespace>

# Describe pod
kubectl describe pod <pod-name>

# Delete pod
kubectl delete pod <pod-name>
kubectl delete -f pod.yaml

# View pod logs
kubectl logs <pod-name>
kubectl logs <pod-name> -c <container-name>  # Specific container

# Execute commands in pod
kubectl exec -it <pod-name> -- /bin/bash
kubectl exec <pod-name> -- <command>
```

## Deployment Operations
```bash
# Create deployment
kubectl create deployment <deployment-name> --image=<image-name>
kubectl apply -f deployment.yaml

# List deployments
kubectl get deployments
kubectl get deploy

# Scale deployment
kubectl scale deployment <deployment-name> --replicas=<number>
kubectl scale deploy <deployment-name> --replicas=3

# Update deployment
kubectl set image deployment/<deployment-name> <container-name>=<new-image>
kubectl rollout status deployment/<deployment-name>

# Rollback deployment
kubectl rollout undo deployment/<deployment-name>
kubectl rollout history deployment/<deployment-name>
```

## Service Management
```bash
# Create service
kubectl expose deployment <deployment-name> --port=<port> --type=<type>
kubectl apply -f service.yaml

# List services
kubectl get services
kubectl get svc

# Describe service
kubectl describe service <service-name>
```

## ConfigMap and Secrets
```bash
# Create ConfigMap
kubectl create configmap <configmap-name> --from-literal=<key>=<value>
kubectl create configmap <configmap-name> --from-file=<file-path>

# Create Secret
kubectl create secret generic <secret-name> --from-literal=<key>=<value>
kubectl create secret generic <secret-name> --from-file=<file-path>

# List ConfigMaps and Secrets
kubectl get configmaps
kubectl get secrets
```

## Resource Management
```bash
# Create resources
kubectl create -f <filename.yaml>
kubectl apply -f <filename.yaml>

# Delete resources
kubectl delete -f <filename.yaml>
kubectl delete <resource-type> <resource-name>

# Get resource info
kubectl get <resource-type>
kubectl describe <resource-type> <name>
```

## Network Policy
```bash
# Create network policy
kubectl apply -f network-policy.yaml

# List network policies
kubectl get networkpolicy
kubectl get netpol
```

## Storage
```bash
# Create PersistentVolume
kubectl apply -f pv.yaml

# Create PersistentVolumeClaim
kubectl apply -f pvc.yaml

# List PV and PVC
kubectl get pv
kubectl get pvc
```

## Imperative Commands Quick Reference
```bash
# Create resources quickly
kubectl run <name> --image=<image>
kubectl create deployment <name> --image=<image>
kubectl expose deployment <name> --port=<port>

# Scale resources
kubectl scale deployment <name> --replicas=<number>

# Update resources
kubectl set image deployment/<name> <container>=<new-image>
```

## Debugging and Troubleshooting
```bash
# Get pod details
kubectl get pods -o yaml
kubectl describe pod <pod-name>

# Check node resources
kubectl top nodes
kubectl top pods

# Port forwarding
kubectl port-forward pod/<pod-name> <local-port>:<pod-port>
```

## Imperative vs Declarative Quick Tips
- Imperative: `kubectl run`, `kubectl create`, `kubectl expose`
- Declarative: `kubectl apply -f <yaml-file>`

## Exam Tips
- Use `kubectl` command-line shortcuts
- Leverage `kubectl explain` for resource definitions
- Practice YAML file creation
- Use `--dry-run=client -o yaml` for generating YAML templates
```

## Useful Shortcuts
```bash
# Create YAML template
kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deployment.yaml

# Quickly generate resource YAMLs
kubectl run nginx --image=nginx --dry-run=client -o yaml
```

## Context and Authentication
```bash
# Switch context
kubectl config use-context <context-name>

# View contexts
kubectl config get-contexts

# Set context namespace
kubectl config set-context --current --namespace=<namespace>
```

# CKA (Certified Kubernetes Administrator) Exam Preparation Checklist

## Exam Coverage Areas (100% Total)
1. Cluster Architecture, Installation & Configuration (25%)
2. Workloads & Scheduling (15%)
3. Services & Networking (20%)
4. Storage (10%)
5. Troubleshooting (30%)

## Essential Commands NOT Fully Covered in Previous Cheat Sheet

### Cluster Installation
```bash
# kubeadm cluster setup commands
kubeadm init
kubeadm join
kubeadm token create
kubeadm upgrade plan
kubeadm upgrade apply
```

### Advanced Resource Management
```bash
# Node management
kubectl cordon <node>
kubectl drain <node>
kubectl uncordon <node>

# Taints and tolerations
kubectl taint nodes <node-name> key=value:NoSchedule
kubectl label nodes <node-name> key=value

# Static Pod creation
# Create pods directly on kubelet
/etc/kubernetes/manifests/
```

### Networking Deep Dive
```bash
# Network policy advanced
kubectl get networkpolicy
kubectl describe networkpolicy

# Service types exploration
kubectl expose deployment <name> --type=NodePort
kubectl expose deployment <name> --type=LoadBalancer
```

### Storage Advanced
```bash
# Storage classes
kubectl get storageclass
kubectl describe storageclass

# Volume management
kubectl create -f persistent-volume.yaml
kubectl create -f persistent-volume-claim.yaml
```

## Recommended Preparation Strategy

### Learning Resources
1. Official Kubernetes Documentation
2. Linux Foundation Course (most recommended)
3. Killer.sh Practice Exams
4. Kubernetes documentation

### Practice Areas
- Cluster setup
- Troubleshooting
- Network policies
- Pod scheduling
- Service configuration
- Persistent volumes
- Security contexts
- Resource quotas

### Practical Skills Needed
- Vim/Nano editing
- Linux command line
- YAML configuration
- Networking concepts
- Troubleshooting skills

## Exam Environment Setup
- Use `kubectl` extensively
- Master imperative and declarative approaches
- Use `kubectl explain` for understanding resources
- Practice creating resources quickly
- Learn shorthand commands

## Exam Tips
- Use `kubectl` shortcuts
- Know how to generate YAML quickly
- Practice time management
- Use `--dry-run=client -o yaml`
- Know how to:
  - Create deployments
  - Scale applications
  - Create services
  - Configure network policies
  - Manage persistent volumes
  - Troubleshoot cluster issues

## Recommended Practice Hours
- 40-60 hours of hands-on practice
- 10-15 complete mock exams
- Minimum 2-3 hours daily practice

## Key Books/Resources
1. Kubernetes Documentation
2. "Kubernetes Up & Running"
3. Linux Foundation CKA Course
4. Killer.sh Practice Exams
5. GitHub Kubernetes Tutorials

### Practice Cluster Environments
- Minikube
- Kind
- k3s
- Katacoda Kubernetes Playground
- Google Kubernetes Engine (GKE)

## Exam Day Preparation
- Use Chrome browser
- Stable internet connection
- External monitor allowed
- One additional browser tab for docs
- Water and comfortable environment
- Minimal background noise
```

## Final Checklist Before Exam
- [ ] Master `kubectl` commands
- [ ] Practice YAML configurations
- [ ] Understand cluster architecture
- [ ] Know troubleshooting techniques
- [ ] Complete multiple mock exams
- [ ] Time management skills
- [ ] Comfortable with Linux terminal

# Kubernetes Command Reference

| Category | Command | Options | Minimal Definition |
|----------|---------|---------|-------------------|
| **Cluster Management** | `kubectl cluster-info` | | Display cluster connection information |
| | `kubectl get nodes` | `-o wide` | List all nodes in the cluster |
| | `kubectl describe nodes` | `<node-name>` | Detailed node information |
| **Namespace Operations** | `kubectl get namespaces` | `-A` | List all namespaces |
| | `kubectl create namespace` | `<name>` | Create a new namespace |
| | `kubectl config set-context` | `--current --namespace=<name>` | Set default namespace |
| **Pod Management** | `kubectl get pods` | `-A`, `-o wide` | List all pods |
| | `kubectl run` | `<pod-name> --image=<image>` | Create a new pod |
| | `kubectl describe pod` | `<pod-name>` | Get detailed pod information |
| | `kubectl logs` | `<pod-name>` | View pod logs |
| | `kubectl exec` | `-it <pod-name> -- /bin/bash` | Execute command in pod |
| **Deployment Operations** | `kubectl create deployment` | `<name> --image=<image>` | Create a deployment |
| | `kubectl get deployments` | | List all deployments |
| | `kubectl scale deployment` | `<name> --replicas=<number>` | Change number of replicas |
| | `kubectl set image deployment` | `<name> <container>=<image>` | Update deployment image |
| | `kubectl rollout undo` | `deployment/<name>` | Rollback to previous deployment |
| **Service Management** | `kubectl get services` | | List all services |
| | `kubectl expose deployment` | `<name> --port=<port> --type=<type>` | Create a service for deployment |
| **ConfigMap & Secrets** | `kubectl create configmap` | `<name> --from-literal=<key>=<value>` | Create configuration map |
| | `kubectl create secret` | `generic <name> --from-literal=<key>=<value>` | Create secret |
| **Resource Management** | `kubectl create` | `-f <filename.yaml>` | Create resources from file |
| | `kubectl apply` | `-f <filename.yaml>` | Apply configuration to resources |
| | `kubectl delete` | `-f <filename.yaml>` | Delete resources |
| **Networking** | `kubectl get networkpolicy` | | List network policies |
| **Storage** | `kubectl get pv` | | List Persistent Volumes |
| | `kubectl get pvc` | | List Persistent Volume Claims |
| **Debugging** | `kubectl describe` | `<resource> <name>` | Get detailed resource information |
| | `kubectl logs` | `<pod-name>` | View container logs |
| | `kubectl top` | `nodes`, `pods` | View resource consumption |

## Quick Exam Tips
- Use `--dry-run=client -o yaml` to generate YAML templates
- Practice both imperative (`kubectl run`) and declarative (`kubectl apply -f`) approaches
- Master `kubectl explain` for resource structure understanding