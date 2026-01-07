## Q1) Can you explain the architecture of a Kubernetes cluster and the components involved?

### Answer  
A Kubernetes cluster consists of a **Control Plane** (API Server, Scheduler, Controller Manager, etcd) and multiple **Worker Nodes** (Kubelet, Kube Proxy, Container Runtime). The control plane manages the cluster state, while the worker nodes run the actual workloads (pods).


## 🧠 1. **Control Plane** — The Brain of the Cluster

The control plane manages and maintains the desired state of the cluster (e.g., which apps are running, what images they use, which nodes they run on, etc.).

### Key components:

| Component          | Purpose |
|-------------------|---------|
| **kube-apiserver** | Entry point to the cluster. All communication (kubectl, controllers) goes through this REST API. |
| **etcd**           | Distributed key-value store for storing all cluster data (configuration, state, secrets, etc.). |
| **kube-scheduler** | Assigns pods to nodes based on resource availability, taints/tolerations, affinities. |
| **controller-manager** | Runs various controllers (e.g., Node, ReplicaSet, Job) to monitor and maintain the desired state. |

## ⚙️ 2. **Worker Nodes** — Where Your Apps Run

Worker nodes are where actual application workloads (pods) are deployed.

### Components on worker nodes:

| Component        | Purpose |
|------------------|---------|
| **kubelet**      | Agent that runs on each node, communicates with the API server, ensures containers are running. |
| **kube-proxy**   | Manages networking rules to route traffic to the correct pod using Services. |
| **Container Runtime** | Responsible for running the containers (e.g., containerd, Docker, CRI-O). |

---
### Question 2 
What happens behind the scenes when you run `kubectl apply -f pod.yaml` to deploy a pod in Kubernetes?

### Answer

### 🔗 Communication Flow (Simplified)

1. You run `kubectl apply -f deployment.yaml`
2. `kubectl` talks to the `kube-apiserver`
3. The API server stores config/state in `etcd`
4. The `scheduler` finds the best node to place the pod
5. The `kubelet` on that node pulls the image and starts the container
6. `kube-proxy` and `service` route traffic to the pod

---
## what k8 Cluster:
Group of worker nodes is called cluster
## kubernetes components running on which ports
 - ETCD is running on port  ---2379
 - Kbuelet is running on port --10250
 - Kube-scheduler is running on port ----10251
 - Kube-controller-manager is running on port ---10252
 - services are running on ports 30000-32677
---

## Difference between docker swam and kubernetes 
  ## Created and maintained by Dotcker Inc
   - It is suitable for small applications
   - It is suitable for 10 to 20 container in pod env
   - To setup cluster is very easy 
   - containers are scaled up and down manually 
   - Scaling is faster than kubernetes
   - Rollback are not automatically done
   ## Kubernetes
   - Create by Google and Now maintained  by the CNFC
   - It is suitable for complex architecture
   - It suitable for  1000 and 2000 containers in prod
   - Based on the traffic containers are scaled up and down automatically
   - Scaling up is easy
   - Rollbacks are automatically done
---
## What is purpose of API Server?
- It acts as the front end for kubernetes. Or it acts as  the Gatekeeper of Kubernetes cluster.Kubectl is used to connect the api server
- Users , management devices and command line interfaces these all are talk to the api server to interact with kubernetes cluster
- The Kubernetes API server validates and configures  the api objects which are pods, services, replicationcontrollers, and Deployments.
---
## what is the purpose of Etcd?
 - It is distributed and reliable key value store used by kubernetes to store all the data  which required to manage the kubernetes cluster
- it stores the entire state of the cluster: its configuration, specifications, and the statuses of the running workloads
---
## What is the purpose of Scheduler ?
- The Kubernetes Scheduler is responsible for deciding which worker node a pod should run on.
- When a new pod is created, the scheduler checks available nodes and assigns the pod to the most suitable node.
- It makes decisions based on CPU and memory requirements, node constraints, affinity/anti-affinity rules, and policies.

Once selected, the scheduler binds the pod to that node and kubelet starts the container.
---
## what is purpsoe of Controllers ?
- The controllers are the brain behind the orchestration. They are responsible for noticing and the responding when containers  nodes and end pointing goes down

- Controllers  making decision to bring up the new containers in such cases
---
## what are Types Of Controllers ?
1)replication controller,
2)endpoints controller,
3)namespace controller, 
4)service accounts controller.
---
## what is Container Runtime ?
- It is the underline software that is used to run the containers. In our case that is happened by the docker
- Example: docker ,rkt,	CRI-O
---
## what is the purose of Kubelet?
- Kubelet is an agent running on every worker node that communicates with the Kubernetes control plane.
- It reads the PodSpec and ensures that containers are created, running, and healthy on the node.
- Kubelet continuously monitors pod status and reports it back to the API serve

## what is purpose of Kube-proxy ?
- Kube-proxy runs on every node in the Kubernetes cluster.
- It manages network rules to enable communication between Services and Pods.
- It routes incoming traffic to the correct pod based on IP address and port.
- It ensures Service networking works inside and outside the cluster.

