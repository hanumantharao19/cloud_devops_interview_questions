## where we are storing credentials in GitLab
Ans:
In GitLab pipelines, credentials should generally be stored at the group level for shared access across projects, at the project level for project-specific secrets, and at the instance level only for global administrative use, following least privilege and security best practices.

## how can we connect form git lab to google cloud
- Step 1: Create Service Account and provide required permission
- step 2: Create Workload Identity Pool
```
gcloud iam workload-identity-pools create gitlab-pool \
  --location="global"
```
- step 3: Create Provider (GitLab)
```
gcloud iam workload-identity-pools providers create-oidc gitlab-provider \
  --location="global" \
  --workload-identity-pool="gitlab-pool" \
  --issuer-uri="https://gitlab.com" \
  --attribute-mapping="google.subject=assertion.sub"
```

- Step 4: Allow GitLab to impersonate SA
```
gcloud iam service-accounts add-iam-policy-binding \
  gitlab-sa@<PROJECT_ID>.iam.gserviceaccount.com \
  --member="principalSet://iam.googleapis.com/projects/<PROJECT_NUMBER>/locations/global/workloadIdentityPools/gitlab-pool/*" \
  --role="roles/iam.workloadIdentityUser"
```
- step 5: Configure GitLab CI/CD variables



## how jenkins pod connect to google cloud 
- step 1 create service account in kubernetes
- step 2 create service account in google cloud
- step 3 map the k8 service account  to google service account through work load indentity
- step 4 k8 service is used to create pod in that pods we have terraform software

note: GKE cluster should enable with workload identity

