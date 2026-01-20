## 1) What AWS services have you worked ?
## Compute & Containers
- EC2, Auto Scaling, Launch Templates
- ECR, EKS
- Lambda (for event-driven automation)
## Networking
- VPC, Subnets, Route Tables
- Internet Gateway, NAT Gateway
- ALB, NLB, Security Groups, NACLs
- Route 53
## Storage
- S3 (versioning, lifecycle policies)
- EBS, EFS
## Backup and snapshots
- Databases
- RDS (MySQL, PostgreSQL)
- DynamoDB
- ElastiCache (Redis)
- IAM (roles, policies, least privilege)
- Secrets Manager / Parameter Store
- CloudTrail
- CodeCommit, CodeBuild, CodeDeploy, CodePipeline
---
## 2) How do you resize an EBS volume in AWS?
- Increase the size of the EBS vloume (EBS only supports increase, not decrease)
- Extend the file system with command
```
resize2fs /dev/xvda1
```
- verify the new size with below command
 ```
 df -h.
```
Note: AWS allows online resizing without stopping the instance.
---
## 3) what is difference between EBS and EFS
## EBS volume
- Block storage attached to a single EC2 instance
- Commonly used for OS disks, databases, and application data
- Requires manual resizing
- Exists within a single Availability Zone
## EFS volume
- Shared file system accessible by multiple EC2 instances
- Used for shared storage like microservices, logs, and CMS
- Automatically scales as data grows
- Highly available across multiple Availability Zones
---
## 4)  What is a NAT Gateway and its purpose?  
- A NAT Gateway allows private EC2 instances to access the internet.
- It blocks incoming traffic from the internet, improving security.
- It is deployed in a public subnet and uses an Internet Gateway.
- Used mainly for OS updates, package downloads, and external API calls.
---
## 5) How do you provide internet access to private instances? (HOW)
- Create a NAT Gateway in a public subnet.
- Attach an Internet Gateway to the VPC.
- Update the private subnet route table to route 0.0.0.0/0 via the NAT Gateway.
- This enables outbound-only internet access
---
## 6) Can you explain what VPC Peering is and why it is used in AWS?
- VPC Peering allows two VPCs to connect and communicate privately using AWS’s internal network.
- It is used to share resources like databases or services between VPCs without going over the public internet.
- It works for VPCs in the same or different accounts/regions, but the IP ranges must not overlap.
- You need to update route tables and security groups to allow traffic between the VPCs

---
## 7) What is an AWS Transit Gateway and why do we use it?
- AWS Transit Gateway is a central hub that connects multiple VPCs and on-prem networks through a single gateway.
- it provides secure communication between VPCs and VPN/Direct Connect networks.
- It also supports centralized routing and transit across accounts or regions.
---
## 8)What is the difference between Network ACLs and Security Groups in AWS?
## Security Groups (SGs)(Stateful)
- Act as virtual firewalls at the instance level.
- If you allow incoming (inbound) traffic to an instance,
- Then the response (outbound traffic) is automatically allowed, even if you didn’t explicitly allow it.
- Rules are allow only (cannot explicitly deny).
- Applied to EC2 instances, ENIs, or other resources.

## Network ACLs (NACLs)(stateless)
- Act as firewalls at the subnet level.
- Stateless: Inbound and outbound rules must be defined separately.
- Can allow or deny traffic.
- Applied to subnets, affecting all resources inside them.
---
## 9) What is the difference between a public subnet and a private subnet in AWS?

## Public Subnet:
- Has a route to the Internet through an Internet Gateway (IGW).
- Instances in a public subnet can directly access the internet.
- Used for web servers, bastion hosts, or NAT Gateways.
## Private Subnet:
- No direct route to the internet.
- Instances cannot be accessed from the internet directly.
- Used for databases, application servers, or any internal resources.
- Can access the internet indirectly via a NAT Gateway or NAT instance.
---

## 10) What are the types of Load Balancers in AWS and how do they work?

## Application Load Balancer (ALB)

- Operates at Layer 7 (HTTP/HTTPS).
- Can route traffic based on URL paths, hostnames, or headers.
- Supports microservices and containerized applications.
- Best for web applications requiring advanced routing.

## Network Load Balancer (NLB)
- Operates at Layer 4 (TCP/UDP).
- Handles millions of requests per second with very low latency.
- Can route traffic based on IP protocol data.
- Best for high-performance applications or static IP requirements.

## Classic Load Balancer (CLB)
- Operates at both Layer 4 and Layer 7, but less flexible.
- Supports basic HTTP/HTTPS and TCP load balancing.
- Mainly for legacy applications; AWS recommends ALB/NLB for new apps.

## 11) What are the different storage classes in AWS S3 and when do you use them?
## S3 Standard
- Used for frequently accessed data.
- High durability, availability, and low latency.

## S3 Intelligent-Tiering
- Automatically moves objects between frequent and infrequent access tiers based on usage.
- Saves cost without impacting performance.

## S3 Standard-Infrequent Access (S3 Standard-IA)
- For data accessed less frequently but still requires rapid retrieval.
-Lower storage cost than Standard.

## S3 One Zone-Infrequent Access (S3 One Zone-IA)
- Stores data in a single AZ.
- Cheaper than Standard-IA but less resilient.

## S3 Glacier & Glacier Deep Archive
- For archival and long-term storage.
- Retrieval can take minutes to hours, but storage cost is very low.

## 12) What are the different types of EC2 instances in AWS and when are they used?

## General Purpose (e.g., t3, t4g, m5)
- Balanced CPU, memory, and network.
- Used for web servers, small databases, and general workloads.

## Compute Optimized (e.g., c5, c6g)
- High CPU performance.
- Best for batch processing, high-performance web servers, or scientific modeling.

## Memory Optimized (e.g., r5, x1e)
- High RAM for memory-intensive applications.
- Ideal for databases, in-memory caching, and real-time analytics.

## Storage Optimized (e.g., i3, d2)
- High disk throughput or IOPS.
- Used for NoSQL databases, data warehousing, or big data workloads.

## GPU / Accelerated Computing (e.g., p3, g4dn)
- Includes GPU or FPGA for heavy computation.
- Used for machine learning, AI, graphics rendering.
---
## 13) What is a VPC Endpoint? Is it the same as a Private Endpoint? 

- VPC Endpoint is the AWS concept for connecting your VPC privately to AWS services or on-premises services without going through the public internet.

## There are two types of VPC Endpoints:

- Interface Endpoint → uses PrivateLink; can connect to AWS services, services in other VPCs, or on-premises services via Direct Connect or VPN.

- Gateway Endpoint → for S3 or DynamoDB; does not use PrivateLink and is only for AWS services.

- AWS PrivateLink is a technology that enables secure, private connectivity between VPCs or services using interface endpoints.
---
## 14 What is Amazon CloudWatch and its purpose?

- Amazon CloudWatch is an AWS monitoring and observability service used to monitor resources, applications, and services in real time.

## Purpose of CloudWatch (Simple English):
- It collects metrics and logs from AWS services like EC2, RDS, Lambda, and applications.
- It helps monitor performance and health (CPU, memory, disk, errors, latency).
- You can set alarms to get alerts when something goes wrong (for example, high CPU usage).
- It helps in troubleshooting and root cause analysis using logs and metrics.

## 15 What is AWS CloudTrail and why is it used?
- AWS CloudTrail is a service that records all API activities and user actions in your AWS account.
- It helps you track who did what, when, and from where in AWS.
- CloudTrail is mainly used for security auditing, compliance, and troubleshooting.
- It stores logs of actions like creating, modifying, or deleting AWS resources.

## 16 What is AWS Secrets Manager and why is it used?

- AWS Secrets Manager is a service used to securely store, manage, and rotate sensitive information such as database passwords, API keys, and tokens.

## Why we use AWS Secrets Manager (Simple English)
- It prevents hardcoding secrets in code or configuration files.
- Secrets are encrypted and securely stored using AWS KMS.
- It supports automatic rotation of credentials (for example, database passwords).
- Applications can securely fetch secrets at runtime using IAM permissions.

## 17 What is the difference between horizontal scaling and vertical scaling in AWS?

## Horizontal Scaling
- it means adding or removing servers based on load.
- In AWS,this is done using Auto Scaling Groups, where more EC2 instances are added when traffic increases and removed when traffic decreases.
- It improves high availability and fault tolerance.

## Vertical Scaling
- it means increasing or decreasing the size of a single server.
- In AWS, this is done by changing the EC2 instance type (for example, from t3.medium to t3.large).
- It is simple but usually requires downtime.


## 18 What is the purpose of an RDS Read Replica?
## Answer
- An RDS Read Replica is a copy of the main database used only for read operations.
- Read replicas allow you to distribute read traffic across multiple database instances instead of sending all reads to the primary database.
- This reduces load on the primary database and improves application performance.


## 19 What is the difference between Amazon RDS and Amazon DynamoDB?
- Amazon RDS is a managed relational database that uses SQL and supports databases like MySQL, PostgreSQL, and Oracle.
- Amazon DynamoDB is a managed NoSQL database designed for fast, scalable, and flexible key-value or document storage.
- RDS is ideal for structured data and complex queries, while DynamoDB is best for high-performance, scalable applications with flexible data models.

## 