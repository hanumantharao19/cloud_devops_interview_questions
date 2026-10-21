##  What security best practices have you implemented in Kubernetes?
-  Implemented RBAC (Role-Based Access Control)
     - Followed least privilege principle
     - Restricted user and service account access
     - Namespace-level access control
     - Disabled anonymous access

-  Enabled Network Policies
   - Restricted pod-to-pod communication
   - Allowed only required traffic between services
   - Reduced lateral movement risk inside cluster

- Secured Containers & Pods
  - Ran containers as non-root user
  - Enabled read-only root filesystem where possible
  - Defined CPU & memory limits
  - Configured liveness and readiness probes

- Image Security & CI Scanning
  - Used trusted base images
  - Enabled vulnerability scanning in CI/CD
  - Avoided “latest” tag usage
  - Used private container registry with authentication

- Cluster Hardening & Encryption
 - Enabled etcd encryption at rest
 - Used TLS for all communications
 - Restricted API server access (private cluster)
 - Enabled audit logging

##  Where and how do you store secrets securely?
-  Used Cloud Secret Manager
   - AWS Secrets Manager / SSM Parameter Store
   - GCP Secret Manager
   - Encrypted using KMS

- Integrated Secrets with Kubernetes
   - Used External Secrets Operator or CSI driver
   - Avoided hardcoding secrets in YAML files
   - Injected secrets securely into pods

-  Enforced Access Control
   - Used IAM roles (IRSA in AWS / Workload Identity in GCP)
   - Restricted access using RBAC

- Followed least privilege principle
   - Enabled Encryption at Rest
   - Enabled etcd encryption
   - Ensured secrets encrypted in cloud storage
   - Avoided storing secrets in Git repositories

- Implemented Secret Rotation & Monitoring
   - Periodic secret rotation
   - Monitored secret access via audit logs
   - Avoided exposing secrets in logs or CI/CD output
