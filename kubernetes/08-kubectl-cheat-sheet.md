1. Cluster & Namespace Information
```
kubectl get nodes
```

Purpose: Shows all worker and master nodes in the cluster.
```
kubectl cluster-info
```

Purpose: Displays cluster control-plane and service endpoints.
```
kubectl get namespaces
```

Purpose: Lists all namespaces in the cluster.

2. Pod Management
```
kubectl get pods
```

Purpose: Lists pods in the current namespace.
```
kubectl get pods -A
```

Purpose: Lists pods across all namespaces.
```
kubectl describe pod <pod-name>
```

Purpose: Shows detailed pod information including events and errors.
```
kubectl logs <pod-name>
```

Purpose: Displays logs of a pod’s main container.
```
kubectl logs <pod-name> -c <container-name>
```

Purpose: Shows logs for a specific container in a multi-container pod.
```
kubectl exec -it <pod-name> -- bash
```

Purpose: Opens a shell inside the running container.

3. Deployments & Workloads
```
kubectl get deployments
```

Purpose: Lists all deployments in the namespace.
```
kubectl describe deployment <deployment-name>
```

Purpose: Displays deployment configuration, status, and events.
```
kubectl scale deployment <deployment-name> --replicas=3
```

Purpose: Manually increases or decreases pod replicas.
```
kubectl rollout status deployment <deployment-name>
```

Purpose: Checks the progress of a deployment rollout.
```
kubectl rollout restart deployment <deployment-name>
```

Purpose: Restarts all pods in a deployment without changing config.
```
kubectl rollout undo deployment <deployment-name>
```

Purpose: Rolls back to the previous deployment version.

4. Services & Networking
```
kubectl get services
```

Purpose: Lists all services in the namespace.
```
kubectl describe service <service-name>
```

Purpose: Shows service details like ports and selectors.
```
kubectl get endpoints <service-name>
```

Purpose: Verifies which pod IPs are backing the service.
```
kubectl port-forward pod <pod-name> 8080:80
```

Purpose: Access a pod locally without exposing it via a service.

5. Apply, Create & Delete Resources
```
kubectl apply -f <file>.yaml
```

Purpose: Creates or updates Kubernetes resources declaratively.
```
kubectl create -f <file>.yaml
```

Purpose: Creates resources (fails if already exists).
```
kubectl delete -f <file>.yaml
```

Purpose: Deletes resources defined in a YAML file.
```
kubectl delete pod <pod-name>
```

Purpose: Deletes a pod (controller recreates it if managed).

6. ConfigMaps & Secrets
```
kubectl get configmaps
```

Purpose: Lists all ConfigMaps.
```
kubectl describe configmap <name>
```

Purpose: Shows key-value configuration data.
```
kubectl get secrets
```

Purpose: Lists secrets in the namespace.
```
kubectl describe secret <name>
```

Purpose: Displays secret metadata (values are base64-encoded).

7. Troubleshooting Commands (Most Important)
```
kubectl get events
```

Purpose: Displays recent cluster and pod events.
```
kubectl get events --sort-by=.metadata.creationTimestamp
```

Purpose: Shows events in time order to find root cause.
```
kubectl get pods -o wide
```

Purpose: Shows pod IPs and node placement.

8. YAML & Debug Utilities
```
kubectl get pod <pod-name> -o yaml
```

Purpose: Outputs the full pod YAML for debugging.
```
kubectl explain pod.spec
```

Purpose: Explains pod fields and configuration options.
```
kubectl edit deployment <deployment-name>
```

Purpose: Edits a resource directly in the cluster.