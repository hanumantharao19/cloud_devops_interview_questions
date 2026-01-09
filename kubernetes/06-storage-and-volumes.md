## Question
What is a PersistentVolume (PV)?
# Answer
- A PersistentVolume (PV) is a piece of storage available in the Kubernetes cluster.
- It is created by the admin or automatically using a StorageClass and represents real storage like EBS, NFS, iSCSI, or GCE Disk
---
## Question
What is a PersistentVolumeClaim (PVC)?
# Answer
- A PersistentVolumeClaim (PVC) is a request for storage made by an application (user).
- The PVC asks for storage size, access mode, and type, and Kubernetes binds it to a matching PV.

## Question
what are the PV access modes ?
# Answer
- ReadWriteOnce -- the volume can be mounted as read-write by a single node
- ReadOnlyMany -- the volume can be mounted read-only by many nodes
- ReadWriteMany -- the volume can be mounted as read-write by many nodes

## Question
PV Reclaim Policies
# Answer
- This defines what happens to the storage after PVC is deleted:

- Retain: Data is kept; admin must clean it manually

- Recycle: Data is deleted (rm -rf) (mostly deprecated)

- Delete: Storage is deleted automatically (EBS, GCE PD, etc.)