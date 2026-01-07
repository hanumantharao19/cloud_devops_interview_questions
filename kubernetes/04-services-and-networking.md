### Question 1
What is a Service in Kubernetes? (Interview intro)

### Answer
In Kubernetes, a Service provides a stable network endpoint to access a set of Pods because Pod IPs are dynamic and keep changing.

---
### Question 2
 what are the type services in kubernetes and explain those

### Answer
- ClusterIP Service
   - ClusterIP exposes the application only inside the Kubernetes cluster.
   - For example, a backend API or database that should be accessed only by other services inside the cluster uses ClusterIP.

- NodePort Service
  - NodePort exposes the service on a static port on each worker node.
  - For example, during development or testing, we can access an application using <NodeIP>:NodePort.
Port range:
30000–32767

- LoadBalancer Service
  - LoadBalancer exposes the application to the internet using a cloud provider load balancer.
  - For example, In production on AWS,GCP or Azure, we use a LoadBalancer service to expose applications publicly

- External Service
  - ExternalName maps a Kubernetes service to an external DNS name, without creating any Pods.
  - For example, if an application needs to connect to an external payment gateway or SaaS API, we use ExternalName.

- Headless Service
   - A Headless Service does not provide load balancing and returns individual Pod IPs directly
   - Headless services are used with StatefulSets like MySQL, MongoDB, or Kafka where each Pod needs a unique identity.

---


### Question  
Explain how you would restrict traffic so that only a specific application (pod) can connect to a database pod within the same namespace.

### Answer
Use a NetworkPolicy to allow database access only from a specific application pod based on labels. Once the policy is applied, all other pods in the same namespace are blocked by default.

Key Points

- By default, all pods can talk to each other

- NetworkPolicy is used to restrict pod-to-pod communication

- Traffic is controlled using labels

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-app-to-db
  namespace: my-namespace
spec:
  podSelector:
    matchLabels:
      role: db
  policyTypes:
  - Ingress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          role: api
    ports:
    - protocol: TCP
      port: 5432
```
---