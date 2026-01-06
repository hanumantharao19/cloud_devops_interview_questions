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

