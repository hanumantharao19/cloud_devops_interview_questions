
### Question
## Difference Between Liveness and Readiness Probes in Kubernetes

---
### Answer  

### 💡 What is a Probe?

Probes are periodic checks Kubernetes performs to determine the state of a container.  
There are three types: `liveness`, `readiness`, and `startup`.

**Liveness probes** check if a container is alive and should be restarted if unresponsive.

```yaml
livenessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 10
  periodSeconds: 5
```  

**Readiness probes** check if a container is ready to receive traffic. If not, it's removed from the service endpoints until it's ready.

```yaml
readinessProbe:
  httpGet:
    path: /ready
    port: 8080
  initialDelaySeconds: 5
  periodSeconds: 3
```
---

### Question  
What are the types of Deployment Strategies which deployment strategy Do You Follow in Your Organization?

### Answer  
In our organization, we primarily follow the **Rolling Update strategy** using **Kubernetes Deployments**, combined with **Canary deployments** via tools like **Argo Rollouts** or **Flagger** for critical services.


### 🔁 1. Rolling Update Strategy (Default in Kubernetes)

This is the default strategy in Kubernetes Deployments:

```yaml
strategy:
  type: RollingUpdate
  rollingUpdate:
    maxSurge: 1
    maxUnavailable: 1
```

- **Old pods are terminated one-by-one**, while **new pods are spun up gradually**.
- Ensures continuous availability with zero downtime.
- Suitable for stateless workloads.

### 🧪 2. Canary Deployment (for critical changes)

For services that are **business-critical or prone to regression**, we use **Canary deployments** via tools like:

- [Argo Rollouts](https://argo-rollouts.readthedocs.io/)

Canary strategy slowly shifts traffic like:

```
10% new version ➜ 50% ➜ 100%
```
#### Benefits:
- We catch issues early with real traffic.
- Automated rollback if metrics or logs indicate failure.

### 🚦 3. Blue-Green Deployment (used less frequently)
- follow below steps to implement the blue-green stratagy
1) Blue environment

 - Current production version
 - Receiving 100% traffic

2) Green environment

 - New application version
 - Deployed but not serving traffic

3) Validation

 - Smoke tests / health checks on Green

4) Traffic switch

- Kubernetes Service selector is changed

- Traffic moves from Blue → Green instantly

5) Rollback

- If issues occur, switch Service back to Blue

### Recreate Deployment Strategy (3–4 lines):
- Recreate strategy stops all existing pods first and then starts new pods with the updated version.This results in application downtime during the transition.

- It is simple to implement and avoids running multiple versions at the same time.
Used mainly for dev/test environments

### Key takeaway  

> "We follow a **Rolling Update** strategy for general use, and **Canary deployments** for critical services. We choose deployment patterns based on service criticality, risk profile, and observability tooling."
---
## What is the purpsoe ConfigMap in kubernetes ?
- A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can 
  consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a 
  volumes 
- A ConfigMap allows you to decouple environment-specific configuration from your container images
---
## waht is the purpose of Secrets in kubernetes ?
- A Secret is an object that contains a small amount of sensitive data such as a password, a token, or 
 a key. 
- Users can create secrets and the system also creates some secrets.
---
## how to resume the deployment ?
`
kubectl rollout resume deployment.v1.apps/nginx-deployment
`
---
## what are the possible reasons for deployment failing ?
- Insufficient quota
- Readiness probe failures
- Image pull errors
- Insufficient permissions
- Limit ranges
- Application runtime misconfiguration
---
## What is the Pod ?

Group of containers is called pod
Most of the cases pod contains single container only but some case pod contains helper container along the main container
If main container dies then  helper container also goes to die
If load on the application Increases then we will not increase no of containers in the pod
Just we are increasing no of pods in the nodes

## what is Node in the kubernetes cluster(k8):
it contains group of pods
If load on the application increases more then we will increase no of workers nodes in the cluster

## what is the difference between Replication Controller and Replication set
  ## Replication Controller;
-------------------
  - Replication  controller  is responsible for making ensure that  the  specified no  of pods (1 or 
    100)running
  - in the nodes at all the time as mentioned in the replication controller
  - The replication controller only supports equality-based selector It has lables
  ## Replication set:
  - the replica set supports set-based selector.
  - It has Match Lables
  - This will help matchExpression to understand the matching condition we have defined and in the 
    operation which is used by matchlabel to find details
  - Kubernetes stores the last 10 ReplicaSets and lets you roll back to any of them.
    If want to store more replicasets mention below line spec
    revisionHistoryLimit: 100
  - This will help matchExpression to understand the matching condition we have defined and in the 
    operation which is used by matchlabel to find details