


🔹 Level 1 – Core DevOps & Cloud Fundamentals
1. Can you introduce yourself?
2. What are the best practices in Ansible?
3. What is the purpose of storing the Terraform state file in Amazon S3?
4. Write a basic Dockerfile.
5. Explain how to build a Docker image and deploy it to Kubernetes using CI/CD
(Write Dockerfile, Kubernetes Deployment manifest, and Jenkins pipeline stages).
6. Write a Terraform configuration to create an S3 bucket.
7. What is Blue/Green deployment?
8. How does a Rolling Update work?
9. How does a Canary Deployment work?
10. What is an Ingress Controller in Kubernetes?
11. What are terraform taint and terraform import, and when do you use them?

🔹 Level 2 – Troubleshooting, Architecture & Experience
1. A pod is continuously restarting and entering CrashLoopBackOff. How would you troubleshoot it?
2. How do you migrate Jenkins to GitHub Actions?
3. You accidentally ran terraform destroy instead of terraform apply. How would you handle this situation?
4. Can you explain your hands-on experience with Kubernetes?
5. What security best practices have you implemented in Kubernetes?
6. Where and how do you store secrets securely?
7. Why are you looking to move on from your current organization?


 How do you configure Jenkins?
▪ How does Blue/Green deployment work?
▪ Is there any downtime in Blue/Green deployment?
▪ A user is unable to access an S3 bucket – how do you troubleshoot?
▪ How do you design a highly available Kubernetes cluster?
▪ How do you serve 50% traffic to Team A and 50% to Team B in Kubernetes?
▪ What are your roles and responsibilities as a DevOps Engineer?
▪ Where do you deploy applications—on-premises or in the cloud?
▪ Write Terraform code to create an S3 bucket
▪ What is a recent Kubernetes issue you troubleshot?
▪ Which command is used to check pod logs?
▪ How does ArgoCD work?
▪ Explain the end-to-end CI/CD workflow using Jenkins
▪ How do you troubleshoot a server that is not working?
▪ What automation have you implemented using Ansible?

🔹 Level 2
▪ How do you list Kubernetes pods based on age?
▪ What is the Terraform workflow?
▪ If a Terraform project has 100 resources, how do you create only one?
▪ Differences between DaemonSet, StatefulSet, and Deployment
▪ What is a headless service and how does it work?
▪ What are Kubernetes probes, and how many types are there?
▪ Can we create a StatefulSet without PV and PVC?
▪ Can we attach PV and PVC to a Deployment?
▪ How do you provide S3 access to an EC2 instance?
▪ What is Backstage and how does it work?
▪ What is APM ( Application Performance Monitoring)?
▪ Do you worked on Observability, Monitoring and Tracing?

Lately I’ve noticed a pattern in DevOps and Cloud interviews.

Interviewers are not only asking about tools anymore.
They are asking how you think when things go wrong.

Questions: 
- What will you check if an application is slow but CPU and memory are normal?
- How do you troubleshoot when everything looks healthy but users see errors?
- How do you approach a production issue step by step?

These questions made me reflect on my own approach.

In real systems, problems rarely come from one place.

It could be networking, DNS, connection limits, dependencies, or configuration drift.

One approach that consistently helps: Start from the user → follow the request path → verify each layer → check recent changes.

Over time I’ve learned: Troubleshooting is less about knowing commands and more about thinking in a structured way.

If you’re preparing for DevOps or Cloud interviews, spend time learning how systems fail, not just how to deploy them.



 1. Production AKS app went down at 2 AM. What is your immediate action plan?
 2. Pods are in CrashLoopBackOff after deployment. How will you troubleshoot?
 3. Deployment works in Dev but fails in Prod. What will you compare first?
 4. Terraform apply failed midway and some Azure resources are created. What next?
 5. Someone modified Azure resource manually which is managed by Terraform. How do you handle drift?
 6. AKS cannot pull image from ACR. How will you debug?
 7. Production pods CPU is 90 percent. What steps will you take?
 8. AKS node shows NotReady. What is your investigation approach?
 9. How will you design zero downtime deployment for critical application?
 10. Azure DevOps pipeline is successful but changes not reflecting in AKS. Where will you check?
 11. How will you structure Terraform for Dev, QA, and Prod environments?
 12. How do you secure secrets in Kubernetes for production workloads?
 13. Cluster autoscaler is not scaling nodes even when CPU is high. What will you verify?
 14. Terraform state file accidentally deleted. What are recovery steps?
 15. How will you configure private AKS cluster with restricted access?
 16. HPA configured but pods are not scaling. What could be wrong?
 17. Production deployment failed and business wants immediate rollback. What is your approach?
 18. How will you migrate manually created Azure infrastructure to Terraform?
 19. CI/CD pipeline taking 40 minutes. How will you optimize it?
 20. Multiple engineers working on same Terraform code. How do you prevent conflicts?
 21. How will you expose AKS app using Application Gateway instead of LoadBalancer?
 22. Ingress configured but traffic not reaching pods. What will you check?
 23. Node showing disk pressure error. How will you fix?
 24. How will you restrict production access only to specific IP addresses?
 25. Application needs persistent storage in AKS. What will you use and why?
 26. After new release, some users still see old version. What could be the issue?
 27. How will you implement Blue Green deployment in AKS?
 28. Security team says AKS cluster is publicly accessible. How will you secure it?
 29. How will you rotate secrets without downtime?
 30. There is complete production outage. How do you handle troubleshooting and stakeholder communication?


 Deployed trained ML models to production using FastAPI + Docker + Kubernetes.
 • Built automated CI/CD pipelines for ML model packaging & deployment (GitHub Actions, Argo, Tekton).
 • Containerized training/inference workflows & optimized image sizes by 30–50%.
 • Leveraged MLflow / Weights & Biases for experiment & model tracking.
 • Managed GPU/CPU resource scheduling for model inference & batch jobs.
 • Integrated monitoring for model latency, throughput, errors & hardware utilization.
 • Instrumented ML services with Prometheus metrics + Grafana dashboards.
 • Implemented A/B and Canary deployments for new model versions.
 • Added Alertmanager → Slack / PagerDuty for real-time anomaly detection.
 • Collaborated with Data Scientists to convert notebooks into production services.


  Designing intelligent rollout & self-healing automation using LangChain agents & Kubernetes
 • Integrated Prometheus metrics with agent-based decision models for anomaly detection & remediation
 • Automated root cause summarization for incidents leveraging LLMs



1️⃣ Running Pods as Root
 ❌ Stop → Allowing privileged containers by default
 ✅ Start → Enforce runAsNonRoot with Pod Security Standards

2️⃣ Wide-Open RBAC Permissions
 ❌ Stop → Using cluster-admin for everything
 ✅ Start → Implement least-privilege with namespace-scoped roles

3️⃣ No Network Segmentation
 ❌ Stop → Allowing pod-to-pod communication by default
 ✅ Start → Deploy Network Policies with default-deny rules

4️⃣ Missing Image Scanning
 ❌ Stop → Pulling untrusted images from public registries
 ✅ Start → Scan images in CI/CD + use admission controllers

5️⃣ Exposed Secrets in ConfigMaps
 ❌ Stop → Storing passwords in plain YAML
 ✅ Start → Use external secret managers (Vault, AWS Secrets Manager)

━━━━━━━━━━━━━━━━━━━━

The gap between knowing these and implementing them? That's where breaches happen.



What is a Terraform state file and why is it important?
How does Terraform state locking work?
What is the difference between local and remote backend?
How do you import an existing resource into Terraform?
What happens if the Terraform state file is deleted?
What is a Terraform module?
How do you call a local module?
What is the purpose of terraform taint or -replace?
How does Terraform handle dependencies between resources?
What are workspaces in Terraform?

AWS
What is Assume Role and how does it work?
What is AWS STS?
Difference between IAM policy and Trust policy?
How does cross-account access work in AWS?
What is a Service Control Policy (SCP)?
What happens if SCP denies but IAM allows?
How do you securely copy S3 data between two AWS accounts?
How does IAM role attached to EC2 work?
Difference between public subnet vs private subnet?
what is EBS, S3, EFS?

🔹 Docker
Write a Dockerfile for a simple web application.
Difference between CMD and ENTRYPOINT?
What is the difference between COPY and ADD?
How do you reduce Docker image size?
What are Docker layers?
how to get running container ip address?

🔹 Scenario-Based
How do you design highly available infrastructure in AWS?
How do you handle secret management securely?
What are best practices for production Terraform usage?
How do you troubleshoot a server that is not reachable?
How do you design cross-account governance in AWS?


1) How do you identify and resolve the high CPU and memory usage in a Linux server?
2) Write a shell script to monitor a process to restart if it is not running.?
3) can you please explain me a situation where you handled Git merge conflict during a hotfix in a live production branch?
4) how do you enforce branch protection and code reviews in a GitHub CI/CD pipelines?
5)what are the strategies you have used to reduce a Docker image size and speed up the build time? 6)how do you handle the persistent data in a Docker containers with real time?
7) how do you ArgoCD fit to GitOps for flow in CI/CD pipelines?
8) how do you configure high availability and application on AWS using easy, ALB, Auto Scaling? 9) how do you monitor the infrastructure, set up alerts in downtime?
9) VPC peering.
10) Where do you guys are maintaining state file?
11)How do you use the Terraform provisioning VPC with public and private subnets?
12) Can you explain me the difference between Terraform taint, refresh, plan?
13) How do you integrate SonarCube code quality checks and Nexus Artifactor with Jenkins pipeline? 14) How do you handle situation where Kubernetes production was going to crash loop backup state? 15) What is your approach zero downtime deployments in Kubernetes?




Continuing the real-world Terraform issues every DevOps engineer eventually faces — and how to fix them fast 👇

✅ Scenario 4: AWS API rate limits hit during deployment
❓ What happens?
Terraform sends too many API requests and AWS throttles them → deployment slows or fails.
💡 Fix:
Retry with controlled parallelism.
🛠 Commands:
terraform apply -parallelism=5
👉 Tip: Reduce parallel execution in large deployments to avoid throttling.

✅ Scenario 5: Manual infrastructure changes cause drift
❓ What happens?

Someone edits resources in the cloud console → Terraform state no longer matches reality.
💡 Fix:
Detect drift and reconcile infrastructure.
🛠 Commands:
terraform plan
terraform apply
👉 Best practice: Avoid manual production changes — always use IaC.

✅ Scenario 6: Resource removed from code but still exists
❓ What happens?
Terraform plans to destroy the resource on next apply.
💡 Fix:
Remove resource from Terraform state if you want to keep it.
🛠 Command:
terraform state rm <resource_name>
👉 Warning: State edits are powerful — double-check before running.

🔥 Save this — these scenarios happen in real production environments, not labs.
Comment if you’ve faced any of these Terraform surprises 👇
Follow for more DevOps real-world breakdowns.



Designing a Single CI/CD Pipeline for Multiple Projects – Is This the Right Approach?
In one of my recent architecture discussions, I explored designing a single reusable CI/CD pipeline to handle multiple projects efficiently.
Here’s the approach:
🔹 Multiple application repositories (or modules)
 🔹 Developers raise feature branches and merge into develop
 🔹 On merge → pipeline detects file/path-level changes
 🔹 Only the impacted project is built and compiled
 🔹 Post successful compilation → Continuous Deployment is triggered automatically
🎯 Core Objective
Instead of maintaining multiple isolated pipelines per project, the idea is to:
Reduce duplication
Improve governance
Standardize quality gates
Optimize build resources
Enable scalable DevOps practices
🏗 Proposed Architecture Pattern
Using platforms like:
Azure DevOps
GitHub Actions
GitLab CI/CD
We can design:
✔ Path-based triggers
 ✔ Conditional stages
 ✔ Template-based YAML reuse
 ✔ Centralized pipeline governance
 ✔ Automated artifact versioning
 ✔ Continuous Deployment to Dev/Test environments
⚙ How It Works
Developer merges feature branch → develop
Pipeline detects changed directories (diff-based execution)
Only impacted module is built
Artifacts are published
CD pipeline deploys automatically (Dev → QA → Prod based on strategy)
🧠 Is This a Best Practice?
In my view, Yes — if designed properly.
However, key considerations include:
🔐 Governance & access control
📦 Monorepo vs multi-repo strategy
⚡ Pipeline performance & parallelization
🧪 Independent versioning of services
🔄 Rollback strategy
📊 Observability & failure isolation
If not architected correctly, a single pipeline can become:
A bottleneck
Hard to troubleshoot
Risky for large teams
💬 I Would Love to Hear From the Community
Have you implemented a centralized pipeline for multiple projects?
Do you prefer independent pipelines per service?
How do you manage change detection and selective builds?
Any challenges with scaling this model?
Looking forward to learning from your experiences.



1. Introduction 
2. Monolithic and Microservices infrastructure
3. How to troubleshoot Out of memory error? 
4. How to setup a CPU utilisation alarm? 
5. How to identify and fix a deadlock situation in an application? 
6. Explain Api in term of microservice architecture? 
7. Distinguish between Application and Infrastructure issues? 
8. How would you troubleshoot ssh related issues? 
9. Differentiate between SLA, SLO, SLI and how would we measure them? 
10. How would you troubleshoot a slow transaction in a microservice architecture?
11. How would you troubleshoot an EC2 instances which is not responding via ssh? 
12. Difference between Security Group and NACL. 
13. Explain 502 and 503 error code. 
14. How to troubleshoot an s3 bucket accessibility issue? 
15. How would you check audit related information for an IAM user?




I’m leading the team at Publicis Sapient responsible for a large-scale CI/CD modernization and migration initiative, leveraging the Slingshot agentic framework to transform how we build and deploy applications. Our work integrates GenAI models like Gemini and GPT, Harness MCP and custom RAG solutions to automate pipeline creation, optimize delivery workflows, and enhance developer experience. We also use Vertex AI to bring intelligence, observability, and scalability into our DevOps ecosystem—helping teams deliver faster, smarter, and more resilient systems.



At Publicis Sapient, I’m part of a team pushing boundaries at the intersection of Generative AI, cloud infrastructure, and automation. My current focus is on GenAI migration and agentic systems, working hands-on with Harness, RAG (Retrieval-Augmented Generation), Vertex AI, MCP server, and the Slingshot agentic framework to help organizations accelerate digital transformation with smarter, scalable, and secure AI-driven solutions.

I come from a background in Electronics and Communications Engineering at Lovely Professional University, and over time, I’ve grown passionate about bringing together DevOps, cloud security, and AI-driven automation across GCP and AWS.

Before joining Publicis Sapient, I worked as a Senior Technical Lead at HCLTech, where I led several cloud modernization and infrastructure optimization projects that boosted performance and resilience.

What keeps me motivated is the challenge of bridging AI innovation with real-world infrastructure—building systems that are not only technically strong but also meaningful in how they empower people and organizations to do more.



Integrating a Claude 4.5-powered AI agent into a secured commercial lending workflow to automate document understanding, decision support, and downstream orchestration across serverless services.

Scope:

Use Amazon Bedrock (Claude Sonnet 4.5) for structured extraction and valuation-oriented reasoning.

Implement Bedrock Guardrails (Terraform-managed, versioned) for policy enforcement and safe output handling.

Orchestrate with AWS Lambda, SQS, API Gateway, DynamoDB, and S3.

Add end-to-end observability (X-Ray, correlation IDs, transaction tracing).

Enforce CI quality/security gates (linting, formatting, security scans, type checks, LangGraph validation).



Production-Level Errors in DevOps – What We See Frequently 🚨


Every DevOps engineer knows that “production” is the ultimate truth.”
 No matter how good your pipelines, tests, and staging environments are, production has its own surprises.

Common production issues in DevOps: 

1. CrashLoopBackOff Pods → Due to misconfigured environment variables, missing dependencies, or bad application code.
2. ImagePullBackOff → Wrong Docker image tag, private registry auth failure.
3. OOMKilled → Container exceeds memory limits.
4. CPU Throttling → Poorly tuned CPU requests/limits or noisy neighbors on the same node.
5. Insufficient IP Addresses → Pod IP exhaustion in VPC/CNI networking.
6. DNS Resolution Failures → CoreDNS issues, network policy misconfigurations.
7. Database Latency/Connection Leaks → Max connections hit, slow queries blocking requests.
8. SSL/TLS Certificate Expiry → Forgot renewal (ACM, Let’s Encrypt).
9. PersistentVolume Stuck in Pending → Storage class misconfigured or no nodes with matching storage.
10. Node Disk Pressure → Nodes running out of disk, causing pod evictions.
11. Node NotReady / Node Evictions → Node failures, taints not handled, or auto-scaling misconfig.
12. Configuration Drift → Infra changes in production not matching Git/IaC.
13. Secrets Mismanagement → Expired API keys, secrets not rotated, or exposed secrets in logs.
14. CI/CD Pipeline Failures → Failed deployments due to missing rollback or bad build artifacts.
15. High Latency in Services → Caused by poor load balancing, bad code, or overloaded services.
16. Network Partition / Split-Brain → Nodes unable to communicate due to firewall/VPC routing issues.
17. Service Discovery Failures → Misconfigured Ingress, Service, or DNS policies.
18. Canary/Blue-Green Deployment Failures → Incorrect traffic shifting causing downtime.
19. Health Probe Misconfiguration → Wrong liveness/readiness probes causing healthy pods to restart.
20. Pod Pending State → Due to resource limits (CPU/Memory not available in cluster).
21. Log Flooding / Noisy Logs → Excessive logging consuming storage or making troubleshooting harder.
22. Alert Fatigue → Too many false alerts causing critical issues to be missed.
23. Node Autoscaling Failures → Cluster Autoscaler unable to provision new nodes due to quota limits.
24. Security Incidents → Unrestricted IAM roles, exposed ports, or unpatched CVEs in container images.
25. Rate Limiting from External APIs → Hitting external service limits, leading to app failures.
26. Time Sync Issues (NTP drift) → Application failures due to inconsistent timestamps across systems.
27. Application Memory Leaks → App not releasing memory, leading to gradual OOMKills.
28. Indexing Issues in ELK/Databases → Queries slowing down due to unoptimized indexing.





