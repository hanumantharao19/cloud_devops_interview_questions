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