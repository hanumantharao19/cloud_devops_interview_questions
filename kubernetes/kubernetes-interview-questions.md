
## Difference between docker swam and kubernetes 
  ## Created and maintained by Dotcker Inc
   Developer community is not big as K8s
   It is suitable for small applications
   It is suitable for 10 to 20 container in pod env
   To setup cluster is very easy 
   containers are scaled up and down manually 
   Scaling is faster than kubernetes
   Rollback are not automatically done
   ## Kubernetes
   Create by Google and Now maintained  by the CNFC
   It has huge developer community
   It is suitable for complex architecture
   It suitable for  1000 and 2000 containers in prod
   To setup cluster is complicated
   Based on the traffic containers are scaled up and down automatically
   Scaling up is easy
   Rollbacks are automatically done
## What is purpose of API Server?
It acts as the front end for kubernetes. Or it acts as  the Gatekeeper of Kubernetes cluster.Kubectl is used to connect the api server
Users , management devices and command line interfaces these all are talk to the api server to interact with kubernetes cluster
The Kubernetes API server validates and configures  the api objects which are pods, services, replicationcontrollers, and Deployments.
It is responsble for expose the  various apis

## what is the purpose of Etcd?
 It is distributed and reliable key value store used by kubernetes to store all the data  which required to manage the kubernetes cluster
it stores the entire state of the cluster: its configuration, specifications, and the statuses of the running workloads

## What is the purpose of Scheduler ?
it is Responsible for distributing the work or containers across multiple Worker nodes. It looks for the newly created containers and assign them to the nodes
Scheduler schedules the pods  based on the specification in the configuration file

The scheduler  schedules the pods based on the resource requirements, quality of service requirements, hardware/software/policy constraints, affinity and anti-affinity specifications, data locality, inter-workload interference, deadlines, and so on.

## what is purpsoe of Controllers ?
The controllers are the brain behind the orchestration. They are responsible for noticing and the responding when containers  nodes and end pointing goes down

Controllers  making decision to bring up the new containers in such cases

## what are Types Of Controllers ?
1)replication controller,
2)endpoints controller,
3)namespace controller, 
4)service accounts controller.
## what is Container Runtime ?
- It is the underline software that is used to run the containers. In our case that is happened by the docker
- Example: docker ,rkt,	CRI-O

## what is the purose of Kubelet?
- It is an agent that is running on each worker node. Agents are responsible for running the 
  containers on the node as expected.

- Kubelet works on the description of containers provided to it in the PodSpec and makes sure that the 
  containers are healthy and running.as described in the PodSpec
  A PodSpec is a YAML or JSON object that describes a pod. The kubelet takes a set of PodSpecs that 
  are provided through various mechanisms (primarily through the apiserver) 
  It takes care of starting, stopping, and maintaining application containers organized into pods as 
  directed by the control plane.
## what is purpose of Kube-proxy ?
kube-proxy is a network proxy that runs on each node in your cluster
 It maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.
It is responsible for routing traffic to the appropriate container based on IP and port number of the incoming request
## What is the Pod ?

Group of containers is called pod
Most of the cases pod contains single container only but some case pod contains helper container along the main container
If main container dies then  helper container also goes to die
If load on the application Increases then we will not increase no of containers in the pod
Just we are increasing no of pods in the nodes

## what is Node in the kubernetes cluster(k8):
it contains group of pods
If load on the application increases more then we will increase no of workers nodes in the cluster

## what k8 Cluster:
Group of worker nodes is called cluster
## kubernetes components running on which ports
 - ETCD is running on port  ---2379
 - Kbuelet is running on port --10250
 - Kube-scheduler is running on port ----10251
 - Kube-controller-manager is running on port ---10252
 - services are running on ports 30000-32677

## differecne between imperative and declarative mode
## imprerative
- kubectl run --image=nginx nginx
- kubectl create deployment --image=nginx nginx

## Declarative
- kubectl create -f deployment.yaml
- kubectl apply -f deployment.yaml

## What are the main feild  it the Kubernetes file:
- It contains mainly four fields : 1) api version:
                                                2) kind:
                                                3) metadata:
                                                4) spec
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


## what is the Persistent Voulme(PV) ?
A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned
by an administrator or dynamically provisioned using Storage Classes

This API object captures the details of the implementation of the storage, be that NFS, iSCSI,

## what is the Persistent volume Claim(PVC)?
---------------------------
A PersistentVolumeClaim (PVC) is a request for storage by a user. 
It is similar to a Pod. Pods consume node resources and PVCs consume PV resources.
Pods can request specific levels of resources (CPU and Memory).

## what are the PV access modes ?
----------------
ReadWriteOnce -- the volume can be mounted as read-write by a single node
ReadOnlyMany -- the volume can be mounted read-only by many nodes
ReadWriteMany -- the volume can be mounted as read-write by many nodes


## what are the Reclaim Policy in PV
Current reclaim policies are:
- Retain -- manual reclamation
- Recycle -- basic scrub (rm -rf /thevolume/*)
- Delete -- associated storage asset such as AWS EBS, GCE PD, Azure Disk, or OpenStack Cinder volume is deleted

## what are the PVC Claim:
-------------
- Claims can specify a label selector to further filter the set of volumes. 
 Only the volumes whose labels match the selector can be bound to the claim. 
 The selector can consist of two fields:
- matchLabels - the volume must have a label with this value
- matchExpressions - a list of requirements made by specifying key, 
  list of values, and operator that relates the key and values. 
  Valid operators include In, NotIn, Exists, and DoesNotExist.

Kubernetes Deployment;
----------------------
# cat siva-deployment.yaml 

## how to increase and decrease the replicas count(sacle in or scale out)
  `
  kubectl scale deployment.v1.apps/nginx-deployment --replicas=10
  `
## how to autoscale the replicas count
`
kubectl autoscale deployment.v1.apps/nginx-deployment --min=10 --max=15 --cpu-percent=80
`

## how to resume the deployment ?
`
kubectl rollout resume deployment.v1.apps/nginx-deployment
`
## what are the possible reasons for deployment failing ?
- Insufficient quota
- Readiness probe failures
- Image pull errors
- Insufficient permissions
- Limit ranges
- Application runtime misconfiguration
## what are kubernet Networking plugins ?
- CNI plugins such as Calico / Weavenet, flannel

## What is the purpsoe ConfigMap in kubernetes ?
- A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can 
  consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a 
  volumes 
- A ConfigMap allows you to decouple environment-specific configuration from your container images
## waht is the purpose of Secrets in kubernetes ?
- A Secret is an object that contains a small amount of sensitive data such as a password, a token, or 
 a key. 
- Users can create secrets and the system also creates some secrets.
 
## Pod Networking:
 1)Every pod should have  an IP Address
 2) Every pod should be able to communicate with  every pod in the same node
 3) Every pod should be able to communicate with every pod on other nodes without NAT

## Q8. What do you understand by load balancer in Kubernetes?
A load balancer is one of the most common and standard ways of exposing service. There are two types of load balancer used based on the working environment i.e. 
- Internal Load Balancer 
- External Load Balancer. 
## Q10.  What do you understand by Cloud controller manager?
The Cloud Controller Manager is responsible for persistent storage, network routing, abstracting the cloud-specific code from the core Kubernetes specific code, and managing the communication with the underlying cloud services. 

##  What is a Headless Service?
- Headless Service is similar to that of a ‘Normal’ services but does not have a Cluster IP. This 
  service enables you to directly reach the pods without the need of accessing it through a proxy.

## What are federated clusters?
- Multiple Kubernetes clusters can be managed as a single cluster with the help of federated clusters. 
  So, you can create multiple Kubernetes clusters within a data center/cloud and use federation to 
  control/manage them all at one place.
## Consider a multinational company with a very much distributed system, looking forward to solving the monolithic code base problem.How do you think the company can solve their problem?
- they can shift their monolithic code base to a microservice design and then each and every 
  microservices can be considered as a container.So, all these containers can be deployed and 
  orchestrated with the help of Kubernetes

## kubenetes commands  
```
kubectl run nginx  --image nginx   ----To run the nginx pod form docker image
kubectl    get    pods    -----> To get the running pods
kubectl   get    nodes    ----> To get the working nodes in the cluster
kubectl describe pods    ----> To know the more information about the pods
kubectl create namespace qa
kubectl get  namespaces
kubectl get pods --namespace=dev
kubectl get deployment --namespace=dev
kubectl create -f nginx-deployment.yaml
kubectl describe deployments nginx-deployment
kubectl rollout status deployment.v1.apps/nginx-deployment
kubectl rollout history deployment.v1.apps/nginx-deployment
kubectl rollout undo deployment.v1.apps/nginx-deployment

```