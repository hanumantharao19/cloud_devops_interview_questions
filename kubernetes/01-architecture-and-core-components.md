## Q1) Can you explain the architecture of a Kubernetes cluster and the components involved?

### Answer  
A Kubernetes cluster consists of a **Control Plane** (API Server, Scheduler, Controller Manager, etcd) and multiple **Worker Nodes** (Kubelet, Kube Proxy, Container Runtime). The control plane manages the cluster state, while the worker nodes run the actual workloads (pods).

---

### Detailed explanation of the answer for readers’ understanding

A Kubernetes cluster is made up of:

---

## 🧠 1. **Control Plane** — The Brain of the Cluster

The control plane manages and maintains the desired state of the cluster (e.g., which apps are running, what images they use, which nodes they run on, etc.).

### Key components:

| Component          | Purpose |
|-------------------|---------|
| **kube-apiserver** | Entry point to the cluster. All communication (kubectl, controllers) goes through this REST API. |
| **etcd**           | Distributed key-value store for storing all cluster data (configuration, state, secrets, etc.). |
| **kube-scheduler** | Assigns pods to nodes based on resource availability, taints/tolerations, affinities. |
| **controller-manager** | Runs various controllers (e.g., Node, ReplicaSet, Job) to monitor and maintain the desired state. |

---

## ⚙️ 2. **Worker Nodes** — Where Your Apps Run

Worker nodes are where actual application workloads (pods) are deployed.

### Components on worker nodes:

| Component        | Purpose |
|------------------|---------|
| **kubelet**      | Agent that runs on each node, communicates with the API server, ensures containers are running. |
| **kube-proxy**   | Manages networking rules to route traffic to the correct pod using Services. |
| **Container Runtime** | Responsible for running the containers (e.g., containerd, Docker, CRI-O). |

---
### 🔗 Communication Flow (Simplified)

1. You run `kubectl apply -f deployment.yaml`
2. `kubectl` talks to the `kube-apiserver`
3. The API server stores config/state in `etcd`
4. The `scheduler` finds the best node to place the pod
5. The `kubelet` on that node pulls the image and starts the container
6. `kube-proxy` and `service` route traffic to the pod

---

### Question 2 
What happens behind the scenes when you run `kubectl apply -f pod.yaml` to deploy a pod in Kubernetes?

### Answer
---

### 🔗 Communication Flow (Simplified)

1. You run `kubectl apply -f deployment.yaml`
2. `kubectl` talks to the `kube-apiserver`
3. The API server stores config/state in `etcd`
4. The `scheduler` finds the best node to place the pod
5. The `kubelet` on that node pulls the image and starts the container
6. `kube-proxy` and `service` route traffic to the pod

---

