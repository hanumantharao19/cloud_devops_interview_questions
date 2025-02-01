Kubernetes (k8s)
- kubectl – Command-line tool for interacting with Kubernetes
clusters
- kubectl get pods – List pods in the current namespace
- kubectl get nodes – List nodes in the cluster
- kubectl get services – List services in the cluster
- kubectl apply -f <file>.yaml – Apply configuration
from a file (e.g., a deployment or pod configuration)
- kubectl create -f <file>.yaml – Create a resource
from a file
- kubectl delete -f <file>.yaml – Delete a resource
defined in a file
- kubectl exec -it <pod_name> -- bash – Execute a
command inside a pod (e.g., open a shell)
- kubectl logs <pod_name> – View the logs of a pod
- kubectl describe pod <pod_name> – Get detailed
information about a pod
- kubectl scale deployment <deployment_name> --
replicas=<number> – Scale a deployment to the desired
number of replicas
- kubectl rollout restart deployment
<deployment_name> – Restart a deployment
- kubectl port-forward pod <pod_name>
<local_port>:<remote_port> – Forward a port from a
pod to localhost