
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