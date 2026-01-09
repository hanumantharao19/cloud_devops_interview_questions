### Question  
What are labels and selectors in Kubernetes and how are they used?

### Answer  
**Labels** are key-value pairs attached to Kubernetes objects for identification, while **selectors** are used to filter or group objects based on their labels. Services, ReplicaSets, and deployments use selectors to manage the right set of pods.

## 🏷️ What are Labels?

Labels are **metadata** assigned to Kubernetes objects such as pods, nodes, services, etc.

```yaml
metadata:
  labels:
    app: frontend
    env: production
```

## 🔍 What are Selectors?

Selectors are **queries** used by other resources to match specific labels. For example, a service can use a selector to send traffic only to pods with a particular label.

```yaml
selector:
  app: frontend
```
---
## Question
How Node Affinity Works in Kubernetes and When to Use It
### Answer  
- Node Affinity allows a pod to be scheduled only on specific nodes based on node labels.
- It is used when a workload must run on particular nodes, such as GPU nodes, SSD nodes, or nodes in a specific zone.


### 🎯 What Is Node Affinity?

Kubernetes nodes can have labels like:

```bash
key = disktype
value = ssd
```

Node affinity lets you **require or prefer** that pods run only on nodes with specific labels.

---

### 🔧 Types of Node Affinity

1. **requiredDuringSchedulingIgnoredDuringExecution**
   - Hard rule: Pod **won’t schedule** unless the rule is met.
   - Example: Only run on GPU nodes.

2. **preferredDuringSchedulingIgnoredDuringExecution**
   - Soft rule: Pod **prefers** to run on a node but can fall back to others.
   - Example: Prefer zone `us-east-1a`, but any zone is okay.

---

### 📦 Example YAML (Required Affinity)

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
      nodeSelectorTerms:
        - matchExpressions:
            - key: disktype
              operator: In
              values:
                - ssd
```


