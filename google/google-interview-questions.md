## 1) What are the different types of IAM roles in Google Cloud? Explain them briefly.
## Answer
- In Google Cloud, IAM roles control what permissions a user or service account has. There are three types of IAM roles:

## Primitive (Basic) Roles

- These are legacy roles like Owner, Editor, and Viewer
- They give very broad permissions across all services
- Not recommended because they are less secure

## Predefined Roles

- Created and managed by Google
- Provide permissions for a specific service or specific service account
- Example: Compute Admin, Storage Object Viewer
- Recommended for most use cases

## Custom Roles

- Created by customers
- You can choose only the required permissions
- Used when predefined roles do not fully meet the requirement
- Best for following the least privilege principle
---
## 2)What are the different types of service accounts in Google Cloud?
## Answer
- In Google Cloud, service accounts are special accounts used by applications and services to access Google Cloud resources. There are three main types:

## User-Managed Service Accounts
- Created and managed by users
- Used by applications running on Compute Engine, GKE, Cloud Run, etc.
- Recommended when you need full control over permissions

## Google-Managed Service Accounts
- Created and managed by Google
- Used internally by Google Cloud services
- Example: default service accounts for services like Compute Engine
- Limited control over permissions

## Default Service Accounts
- Automatically created when you enable a service or create a project
- Example: Compute Engine default service account
- Often has broad permissions, so should be used carefully
---
## 3) What are the different types of Compute Engine instances in Google Cloud?
## Answer
- In Google Cloud, Compute Engine instances are virtual machines used to run applications. The main types are:

## General-Purpose Instances

- Balanced CPU and memory
- Used for web servers, small databases, and common applications
- Example: E2, N2, N1

## Compute-Optimized Instances

- More CPU power
- Used for high-performance computing and batch processing
- Example: C2, C2D

## Memory-Optimized Instances

- Large memory compared to CPU
- Used for in-memory databases and large analytics
- Example: M1, M2

## Accelerator-Optimized Instances

- Designed for GPU workloads
- Used for machine learning, AI, and graphics processing
- Example: A2

---
## 4) What is the difference between Managed Instance Groups and Unmanaged Instance Groups in Google Cloud?

## Answer

- In Google Cloud, Instance Groups are collections of virtual machine instances. The key differences are:

## Managed Instance Groups (MIG)

- All VMs are identical and created from an instance template
- Supports auto-scaling, auto-healing, and load balancing
- Google Cloud automatically manages VM creation, updates, and recovery
- Best for stateless applications and production workloads

## Unmanaged Instance Groups (UMIG)
- VMs can be different from each other
- No auto-scaling or auto-healing
- You manually add, remove, and manage instances
- Best for legacy or stateful applications
---
## 5) What is the difference between a Host Project and a Service Project in Google Cloud?

- In Google Cloud, Host Project and Service Project are used in a Shared VPC setup.

## Host Project
- Contains and manages the Shared VPC network
- Owns subnets, firewall rules, and routes
- Provides network resources to other projects
- Controlled mainly by network administrators

## Service Project

- Uses the network from the Host Project
- Runs workloads like Compute Engine, GKE, and Cloud Run
- Does not create or manage network resources
- Focuses on application and service deployment

---
## 6) What is the Hub-and-Spoke network model in Google Cloud?

## Answer

- The Hub-and-Spoke model is a network architecture in Google Cloud that centralizes shared services and connectivity while keeping workloads separate.

## The Hub

- A central VPC (Virtual Private Cloud) that acts as the main routing gateway

- Hosts shared resources such as:

 - Connections to on-premises networks (via Cloud VPN or Interconnect)

 - Shared services like DNS, Active Directory, or firewalls

 - Egress control with Cloud NAT or proxy appliances for internet access

 - Centralizes security, logging, and traffic management

## The Spokes

- Multiple isolated VPCs connected to the hub

- Each spoke contains workloads like production, development, or separate business units

- Ensures security and billing isolation

## Why It’s Useful:

- Centralized Security: Policies and traffic inspection are managed at the hub

- Scalability: Adding new workloads is easy—just connect a new spoke to the hub

- Isolation: Spokes are separate, so workloads don’t interfere with each other
---
## 7 What is Google App Engine, and what is its purpose?
## answer
- Google App Engine (GAE) is a fully managed Platform-as-a-Service (PaaS) in Google Cloud that lets you build and run applications without managing the underlying infrastructure.

## Purpose / Key Benefits:

- No Infrastructure Management: You don’t need to worry about servers, scaling, or OS patches.

- Automatic Scaling: Applications automatically scale up or down based on traffic.

- Supports Multiple Languages: Python, Java, Node.js, Go, PHP, .NET, and custom runtimes.

- Built-in Services: Datastore, Cloud SQL, caching, and logging are integrated for easy use.

- Focus on Code: Developers can focus on writing application logic rather than managing servers.
---

## 8) What is Google Cloud Functions, and what is its purpose?
## Answer
- Serverless compute service to run small pieces of code in response to events.
- Automatically scales based on demand, no need to manage servers.
- Supports multiple languages like Node.js, Python, Go, and Java.
- Ideal for event-driven tasks like file processing, API triggers, or sending notifications
---
## 9) what is Difference Between App Engine and Cloud Functions

- Scope: App Engine runs full applications or APIs, while Cloud Functions runs small code snippets triggered by events.

- Use Case: App Engine handles entire applications, Cloud Functions handles single tasks like responding to HTTP requests, Pub/Sub messages, or storage events.

- Ideal For: Cloud Functions is ideal for event-driven tasks (e.g., file processing, notifications, lightweight APIs).

- App Environment: App Engine provides a complete application environment with built-in services and supports longer-running processes.
---
## 10 What is Google Cloud Run, and what is its purpose?
- Fully managed service to run containerized applications without managing servers.
- Automatically scales up or down based on traffic.
- Supports any language or library inside a container.
- Ideal for running microservices, APIs, or stateless applications that need fast deployment.
---
## 11 What are the types of GKE clusters in Google Cloud, and what is their purpose?

## Standard Cluster
- Default type of GKE cluster
- Gives full control over node management and cluster configuration
- Ideal for workloads that need custom node setup or flexibility

## Autopilot Cluster
- Fully managed, serverless mode of GKE
- Google manages nodes, scaling, and maintenance automatically
- Ideal for developers who want to focus on applications, not infrastructure

## Private Cluster
- Master (control plane) is isolated from the public internet
- Nodes communicate securely via private IP
- Ideal for high-security environments

## Regional Cluster
- Nodes spread across multiple zones in a region
- Provides high availability and fault tolerance
- Ideal for critical workloads needing minimal downtime
---
## 12 How do you secure a GKE (Google Kubernetes Engine) cluster in Google Cloud?
## Answer
- Use private clusters so nodes and control plane are not exposed to the public internet.

- Control access with IAM and RBAC to give users and services only required permissions.

- Enable network security using VPC firewall rules, Network Policies, and Private Service Access.

- Protect workloads with Workload Identity, Pod Security standards, and container image scanning.
---
## 13 Where is the GKE control plane hosted – in Google’s network or the customer’s network?
## Answer
- The GKE control plane is always hosted in Google’s managed network, not in the customer VPC.
- Google manages and secures the control plane components like the API server, scheduler, and controller manager.
- Customer workloads (worker nodes and pods) run in the customer’s VPC network.
- In private clusters, the control plane is still in Google’s network but is accessible only through private IP connectivity.
---
## 14 What is Google Cloud Composer, and what is its purpose?
## Answer
- Google Cloud Composer is a fully managed workflow orchestration service based on Apache Airflow.
- It is used to schedule, monitor, and manage data pipelines and complex workflows.
- It integrates easily with Google Cloud services like BigQuery, Cloud Storage, and Dataproc.
- It removes the need to manage Airflow infrastructure, letting teams focus on workflow logic.
---
## 15 What is Google BigQuery, and what is its purpose?
## Answer
- Google BigQuery is a fully managed, serverless data warehouse in Google Cloud.
- It is used to store and analyze large amounts of data using SQL queries.
- It automatically scales and delivers fast query performance without managing infrastructure.
- It is mainly used for data analytics, reporting, and business intelligence.
---
## 16 What is Google Cloud Dataflow, and what is its purpose?
## Answer
- Google Cloud Dataflow is a fully managed service for data processing pipelines.
- It is used for batch and real-time (streaming) data processing.
- It is based on Apache Beam, so the same code can run in different environments.
- It automatically handles scaling, resource management, and fault tolerance.
---
## 17 What is Google Cloud Dataproc, and what is its purpose?
## Answer
- Google Cloud Dataproc is a fully managed service for running Apache Spark and Hadoop clusters.
- It is used to process large datasets using big data frameworks.
- Clusters can be created and deleted quickly, helping reduce costs.
- It integrates with services like Cloud Storage and BigQuery for data analytics.
---
## 18 What is Google Bigtable, and what is its purpose?
## Answer
- Google Bigtable is a fully managed, NoSQL wide-column database.
- It is designed to handle very large amounts of structured data with low latency.
- It is ideal for real-time analytics, IoT data, and time-series data.
- Fully managed, scalable, and integrates with services like BigQuery and Dataflow.
---
## 19 What is Google Cloud Spanner, and what is its purpose?
## Answer
- Google Cloud Spanner is a fully managed, relational, globally distributed database.
- Combines SQL support with horizontal scalability and high availability.
- Ideal for mission-critical applications that need strong consistency across regions.
- Handles large-scale transactional workloads without managing infrastructure.
---
## 20 What is Google Cloud SQL, and what is its purpose?
## Answer
- Google Cloud SQL is a fully managed relational database service.
- Supports databases like MySQL, PostgreSQL, and SQL Server.
- Automatically handles backups, replication, patching, and scaling.
- Ideal for web applications, transactional workloads, and business applications.
---
## 21 what is difference between cloud spanner and cloud sql in google cloud
## Answer
- Cloud SQL is a managed relational database for small to medium workloads within a single region.
- Cloud Spanner is a globally distributed relational database for large-scale, mission-critical applications.
- Cloud Spanner provides strong consistency and high availability across regions, while Cloud SQL is simpler and easier for standard apps.

## 22 What are the different storage classes in Google Cloud, and when should we use each one?
## Answer

## Standard Storage
- Used for frequently accessed data
- Best for active data like websites, mobile apps, and analytics

## Nearline Storage
- Used for data accessed less than once a month
- Best for backups and short-term archival

## Coldline Storage
- Used for data accessed once a quarter or less
- Best for disaster recovery and long-term backups

## Archive Storage
- Lowest-cost storage for data accessed rarely (once a year or less)
- Best for long-term data retention and compliance
--- 
## 23 What are the different types of disks in Google Cloud, and what is their purpose?
## Answer

## Standard Persistent Disk (pd-standard)
- HDD-based storage
- Used for low-cost, less performance-critical workloads

## Balanced Persistent Disk (pd-balanced)
- Balanced cost and performance
- Used for general-purpose applications and databases

## SSD Persistent Disk (pd-ssd)
- High-performance SSD storage
- Used for high I/O workloads like databases and analytics

## Local SSD
- Physically attached to the VM
- Used for very high performance and temporary data (data lost on VM stop)
---
## 24 What are the different types of load balancers available in Google Cloud, and when should each be used?
## Answer

## HTTP(S) Load Balancer

- Global, external load balancer for web applications and APIs
- Provides SSL termination and routes traffic based on URL or hostname

## TCP/SSL Proxy Load Balancer

- Global, external load balancer for non-HTTP traffic
- Used when SSL offloading or proxy-based TCP traffic is required

## Network Load Balancer

- Regional, external load balancer for TCP/UDP traffic
- Offers very low latency and handles traffic at the network level

## Internal Load Balancer

- Regional, internal load balancer for services inside a VPC
- Used for private, internal applications and microservices
---
## 25 What is Identity-Aware Proxy (IAP) in Google Cloud, and what is its purpose?
## Answer
- Identity-Aware Proxy (IAP) is a security service that controls access to applications.
- It verifies user identity and permissions before allowing access.
- It works without exposing applications directly to the public internet.
- Used to protect web apps and APIs running on Google Cloud or on-premises.
---

## 26 What is Workload Identity in Google Cloud, and why is it used?
## Answer
- Workload Identity lets applications access Google Cloud services securely.
- It removes the need to use service account key files.
- Google automatically provides short-lived credentials to the workload.
- Commonly used with GKE, Cloud Run, and Compute Engine

## Example
- Allow a Kubernetes workload in GKE to access Google Cloud services (e.g., Cloud Storage) securely without using service account keys.
## proccess(example)
- Create a Google Service Account with required permissions.
- Enable Workload Identity on the GKE cluster.
- Create a Kubernetes Service Account.
- Bind the K8s SA to Google SA.
- Annotate the K8s SA with the Google SA.
- Deploy the pod using the K8s SA, and it can access GCP services securely.
---
## 27 What is Workload Identity Federation in Google Cloud, and what is its purpose?
## Answer
- Workload Identity Federation is a feature of Workload Identity that allows external workloads (AWS, Azure, on-premises, or other clouds) to access Google Cloud resources without using service account keys.
- External identities authenticate using federated tokens (OIDC or SAML), which Google Cloud verifies before granting temporary credentials.
- It improves security by eliminating long-lived keys and providing temporary, auditable access.
- Commonly used for CI/CD pipelines, external cloud services, or hybrid/multi-cloud workloads..
## example:
- A CI/CD pipeline running in AWS needs to upload artifacts to Google Cloud Storage.
- Instead of using a service account key file, the pipeline uses Workload Identity Federation to authenticate securely using its AWS identity.
---
## 28 What is Google Cloud Pub/Sub, and what is its purpose?
## Answer
- Google Cloud Pub/Sub is a messaging service that allows applications to send and receive messages asynchronously.
- It enables decoupling of services — producers (senders) and consumers (receivers) don’t need to know about each other.
- Automatically scales to handle large volumes of messages in real-time.
- Commonly used for event-driven applications, streaming data pipelines, and system integrations.
---
## 29 How can you connect Google Cloud to an on-premises network or service?
## Answer

## Cloud VPN:
- Creates a secure IPsec VPN tunnel over the internet.
- Suitable for small to medium traffic and quick setup.

## Cloud Interconnect:
- Provides a dedicated private connection between GCP and on-premises.
- Offers high bandwidth and low latency, ideal for large workloads.

## Direct Peering / Partner Interconnect:
- Connect via Google’s partner networks for enterprises needing reliable private connectivity.

## Hybrid Access with Private Services Access:
- Allows on-prem services to access Google-managed services privately over VPC.
---
## 30 What is Google Secret Manager, and what is its purpose?
## Answer
- Google Secret Manager is a secure storage service for sensitive information like API keys, passwords, and certificates.
- It allows centralized management, versioning, and access control for secrets.
- Only authorized identities (users or workloads) can access the secrets using IAM permissions.
- Helps keep secrets out of code and configuration files, improving security and compliance.
---
## 31 What is Google Cloud KMS (Key Management Service), and what is its purpose?
## Answer
- Google Cloud KMS is a managed service for creating, storing, and managing cryptographic keys.
- It is used to encrypt and decrypt data securely in Google Cloud services or your applications.
- Provides centralized key management, rotation, and access control via IAM.
- Helps ensure data security, compliance, and auditability.

## 32 How can you connect to a private GKE cluster from your local machine?

## Method 1: VPN or IAP Tunnel

- Use this when you want direct access from your laptop.
- Private GKE clusters have nodes without public IPs, so you can’t access them directly.

## Options:1
 - Cloud VPN: Connects your laptop or on-prem network to the VPC.
or 
## Options:2
 - IAP TCP Tunnel: Securely tunnels kubectl traffic over the internet.
 ## Configure kubectl using:
 ```
 gcloud container clusters get-credentials <cluster-name>
```
## Method 2: Access via Bastion/Jump Host (Optional)

- Set up a VM in the same VPC as the private cluster.

- SSH into the VM from your laptop and run kubectl from there.

## If the control plane has a public endpoint:
- Add the bastion VM’s public IP to the authorized networks list.
## If the control plane only has a private endpoint:
- The bastion VM just needs network access within the VPC; no public IP is required.
---
## 33 How can you connect to a Google Cloud SQL database from your local machine?

## Using Cloud SQL Auth Proxy (Recommended):
- Run Cloud SQL Auth Proxy on your local laptop to create a secure IAM-based connection to Cloud SQL.
- The proxy exposes the database on localhost, so no IP whitelisting or SSL configuration is needed.
- You still connect using a database username and password (Proxy does not replace DB authentication).

## Using Public IP with Authorized Networks:
- Enable public IP on the Cloud SQL instance.
- Add your laptop’s public IP to the authorized networks list.
- Connect using standard DB tools with username and password.

## Using Private IP (via VPN or Interconnect):

- Configure Cloud SQL with a private IP.
- Connect your laptop to the VPC using Cloud VPN or Interconnect.
- Access the database using its private IP address.
---

## how cloud run is connect to the coud Sql database
Cloud Run connects to Cloud SQL either using the built-in Cloud SQL Connector, which securely connects through a Unix socket using IAM permissions, or via a Serverless VPC Connector when Cloud SQL is configured with a private IP. The recommended method is using the Cloud SQL Connector for secure and simplified connectivity.



## what is difference google privatge access and google private connect

- Private Service Access is used to access Google managed services 
  (like Cloud SQL) privately from your VPC.

- Private Service Connect is used to access services across VPCs, 
  projects, or organizations using private endpoints.


  ### Prodcution grade cloud run application access ###
  Ans:
  - step 1:  create cloud run service through terraform 
  - Step 2: create server less network endpoint groups through terraform . that will connect to cloud run serves which we have create in step 1
  - step 3: create backend services . these backend service map to network endpoint groups
 - step 4: For url maps created host based routing through terraform . where domains are maps to backend services
 - step 5: create ssl certificates
 - step 6: create https proxy
 - steps 7 :  create public ip and forward rules where forwarding rules map to public ip
 - steps 8 : create cloud armor and those polacies attached to the backed services

 ## cloud armor will attach to the internal load balancer or external loadbalancer
 Ans:
 Cloud Armor policies are applied at the backend service level of an external HTTP(S)
 - cloud armor is used to block the ip address
 - cloud armor have option only allow india traffic or deny usa traafic
 - cloud armor user api rate limit per minute


 ## what are the authrised views in bigquery
 Ans: 
 “Authorized Views in BigQuery provide controlled access to underlying datasets by exposing only filtered or selected data through views without granting direct table access.”

 ## Purpose of Dataflow (Points)

1️⃣ Real-time (streaming) data processing

Processes live data from sources like Cloud Pub/Sub

2️⃣ Data transformation

Converts raw data into structured, usable format

3️⃣ Batch data processing

Handles large datasets from storage (like files or tables)

4️⃣ Data enrichment

Adds additional information (timestamps, user info, etc.)

5️⃣ Filtering and validation

Removes unwanted or invalid data

6️⃣ Aggregation and analytics

Performs calculations (count, sum, average, windowing)

7️⃣ ETL / ELT pipeline processing

Moves and transforms data between systems (e.g., Pub/Sub → BigQuery)


## vpc service controllers purpose in google cloud
Ans: 
“VPC Service Controls provide a security perimeter around Google Cloud services to protect sensitive data from unauthorized access and data leakage.”





















## What KPIs would you include in a Grafana dashboard?

I would include Golden Signals such as latency, traffic, errors, and saturation. Additionally, I would monitor infrastructure metrics like CPU and memory usage, Kubernetes metrics like pod health and restarts, and database metrics like active connections and query latency. The goal is to detect performance degradation before it impacts users.

## what are gateway we are using in kubernetes to access the application through internet



## How are your GKE pod logs visible in Cloud Logging?

In GKE, a logging agent like Fluent Bit runs on each node and collects container logs from stdout and stderr. These logs are automatically forwarded to Cloud Logging, where they can be viewed in Logs Explorer with Kubernetes metadata attached.



## How do logs from multiple applications on different nodes reach Google Logs Explorer?

In GKE, a logging agent like Fluent Bit runs as a DaemonSet on each node. It collects container logs from stdout and stderr and forwards them to Cloud Logging automatically. No special annotation is required unless custom log routing is needed.



## If your app scales to 15 pods, how are logs and metrics handled?

In GKE, container logs are stored on the node filesystem and collected by Dynatrace OneAgent running as a DaemonSet. The agent automatically discovers new pods and collects logs, metrics, and traces. Data is sent to the Dynatrace server where AI-based monitoring detects anomalies such as memory leaks or excessive garbage collection and raises incidents.

In GKE, a logging agent like Fluent Bit runs as a DaemonSet on each node. It collects container logs from stdout and stderr and forwards them to Cloud Logging automatically. No special annotation is required unless custom log routing is needed.

## How do you reduce Cloud Logging cost?

I would reduce ingestion by lowering log verbosity, creating exclusion filters for non-critical logs, reducing retention for non-production environments, and exporting logs to cheaper storage like Cloud Storage. Controlling log volume at the application level is the most effective strategy

## Why use OpenTelemetry if Prometheus is already there?

Prometheus focuses on metrics collection, whereas OpenTelemetry provides standardized instrumentation for metrics, traces, and logs. In microservices environments, OpenTelemetry helps generate distributed tracing and vendor-neutral telemetry that can be exported to multiple backends, including Prometheus.

## Have you worked on OpenTelemetry?
I have not implemented OpenTelemetry directly, but I understand that it is used for standardized instrumentation of metrics, logs, and traces in distributed systems. In my projects, we used Prometheus and Dynatrace for observability, but I am familiar with how OpenTelemetry integrates with such tools.

##  If They Ask: “How Does It Work?”
OpenTelemetry SDK is added to the application to generate telemetry data such as metrics and traces. This data is collected by an OpenTelemetry Collector, which then exports it to monitoring systems like Prometheus or tracing tools like Jaeger.

## what openTelemetry
OpenTelemetry is an open-source observability framework that standardizes the generation and export of metrics, logs, and distributed traces in cloud-native applications.

## What are the three pillars of SRE?
The three pillars of SRE observability are metrics, logs, and traces. Metrics provide numerical performance data, logs provide detailed event information, and traces provide end-to-end request visibility across distributed systems.

## Which API Gateway does Google Cloud use?
Google Cloud provides a managed API Gateway service for exposing APIs using OpenAPI specifications. For enterprise-level API management, Google also offers Apigee, which provides advanced API lifecycle management and policy control.

## How would you use Apigee with 10 GKE applications?
I would expose each GKE service through an ingress or load balancer, then create API proxies in Apigee that forward requests to the appropriate backend services. Apigee would handle authentication, rate limiting, and security policies, while GKE handles the application logic. Traffic flows from client to Apigee, then to the GKE ingress, and finally to the target service.


## In a cluster with 30 namespaces and many apps, do you deploy multiple ingress controllers?

Typically, a single ingress controller can manage multiple ingress resources across namespaces in a cluster. Multiple ingress controllers are used only when traffic segregation, security isolation, or different ingress technologies are required.

