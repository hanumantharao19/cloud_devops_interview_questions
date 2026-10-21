## commands
- kubectl get nodes
- kubectl get pods -n <namespace>
- kubectl get ns
- kubectl get configmap -n <namespace>
- kubectl get secrets -n <namespace>
- kubectl get services -n <namespace>
- kubectl get pv 
- kubectl get pvc -n <namespace>
- kubectl get netpol -n <namespace>
 or
- kubectl get netol -A  # list in the all namespaces
- kubectl get ingress <namespace>
- kubectl get  deployment <namespace>
- kubectl describe pod <pod name> -n <namespace>
- kubectl describe node <nodename>
- kubectl rollout restart deployment <deployment-name>
- kubectl scale deployment <deployment-name> --replicas=3
- kubectl exec -it <pod-name> -- bash
- kubectl logs <pod-name> -c <container-name>
- kubectl logs <pod-name>
- kubectl cluster-info
- kubectl cordon <node-name>
- kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data
- kubectl taint nodes node-1 env=dev:NoSchedule

