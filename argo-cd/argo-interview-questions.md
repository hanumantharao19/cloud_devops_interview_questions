
## 1. What is Argo CD and why is it used?

## Answer:
- Argo CD is a GitOps-based continuous delivery tool for Kubernetes. It deploys applications by syncing the cluster state with the desired state stored in Git.

## 2. What is GitOps and how does Argo CD implement it?

## Answer:
- GitOps means Git is the single source of truth. Argo CD continuously watches Git and automatically applies changes to Kubernetes clusters.

## 3. What problems does Argo CD solve in Kubernetes deployments?

## Answer:
- It solves manual deployment errors, configuration drift, and lack of visibility by automating deployments from Git.

## 4. How is Argo CD different from Jenkins?
## Answer:
- Jenkins is mainly for CI (build and test), while Argo CD is for CD (deploying to Kubernetes) using GitOps.

## 5. What are the main components of Argo CD?

## Answer:

- API Server
- Repository Server
- Application Controller
- Redis (cache)

## 6. How does Argo CD communicate with Kubernetes clusters?
## Answer:
- Argo CD uses the Kubernetes API server and service accounts to deploy and manage applications.

## 7. What is the role of the Argo CD API server?
## Answer:
- It provides UI, CLI, and REST API access for managing applications and authentication.

## 8. Where does Argo CD store application state?
## Answer:
- Desired state is stored in Git, and live state is read from the Kubernetes cluster.

## 9. What is an Argo CD Application?
## Answer:
- An Application is a custom resource that defines where the code lives (Git repo), where it should deploy, and how it should sync.

## 10. What types of manifests are supported by Argo CD?
## Answer:
- Plain YAML
- Helm charts
- Kustomize
- Jsonnet

## 11. What is the difference between manual sync and auto sync?
## Answer:
- Manual sync: User triggers deployment
- Auto sync: Argo CD automatically applies changes from Git

## 12. What does desired state and live state mean?

## Answer:
- Desired state: Configuration in Git
- Live state: What is currently running in the cluster

## 13. What is configuration drift and how does Argo CD detect it?
## Answer:
- Drift happens when someone changes resources manually. Argo CD detects it by comparing Git state with cluster state.

## 14. How do you perform a rollback in Argo CD?
## Answer:
- Rollback is done by reverting Git to a previous commit and syncing the application.

## 15. What happens if someone manually changes a Kubernetes resource?
## Answer:
- Argo CD marks the app as OutOfSync and can automatically revert the change if auto-sync is enabled.

## 16. How does Argo CD handle authentication and authorization?
## Answer:
- Authentication via SSO, OAuth, LDAP, or local users
- Authorization via RBAC policies

## 17. How can you manage secrets securely with Argo CD?
## Answer:
- Use Kubernetes Secrets, Sealed Secrets, or external secret managers like HashiCorp Vault.

## 18. Can Argo CD deploy to multiple Kubernetes clusters? How?
## Answer:
- Yes. Argo CD supports multi-cluster deployments by registering external clusters and using different application destinations.

## 19. How would you deploy apps to dev, test, and prod environments?
## Answer:
- Use separate Git branches or directories and define different Argo CD applications for each environment.

## 20. What are best practices for using Argo CD in production?
## Answer:
- Use RBAC and SSO
- Enable auto-sync with pruning carefully
- Use separate projects for environments
- Store secrets securely