# SRE Scenario-Based Interview Questions and Answers

## 1. Observability, Monitoring and Alerting

### Q1. Website latency increased from 200 ms to 3 seconds, but CPU and memory are normal. What would you do?

**Answer:**

I would check p95 latency, error rates, and distributed traces in Datadog or Dynatrace. Since CPU and memory are normal, I would investigate database queries, connection pools, external APIs, and network latency. If the issue started after a deployment, I would investigate that change and roll it back if necessary. After recovery, I would fix the root cause and add appropriate alerts.

### Q2. Datadog shows HTTP 5xx errors, but all Kubernetes pods are healthy. How would you troubleshoot?

**Answer:**

Healthy pods don't always mean the application is working properly. I would check application logs, distributed traces, ingress and load balancer logs, and downstream dependencies. For example, the database might be failing even though all pods are running. I would identify the failing component, restore service, and improve health checks and alerts.

### Q3. You receive 500 alerts within 10 minutes because of one database issue. What would you do?

**Answer:**

I would identify the primary alert and check whether the remaining alerts are symptoms of the same database problem. I would configure alert grouping, deduplication, and appropriate notification routing. I would prioritize alerts based on customer impact and SLOs to reduce noise without missing critical incidents.

### Q4. Application logs are missing from GCP Cloud Logging. How would you troubleshoot?

**Answer:**

I would first check whether the application is generating logs. Then I would verify the GKE logging agent, service account permissions, project and resource filters, and log exclusions. I would also check for ingestion or quota issues. After fixing the problem, I would add monitoring to detect missing logs early.

## 2. SLIs, SLOs and Production Readiness

### Q5. Your service has a 99.9% availability SLO but has experienced several outages. What would you do?

**Answer:**

I would check the availability SLI and calculate how much error budget we have consumed. For a 30-day month, a 99.9% time-based SLO allows approximately 43 minutes of downtime. I would review incidents, identify recurring failure patterns, and prioritize fixes based on customer impact. I would also improve alerting, deployment safety, and recovery procedures.

### Q6. A developer wants to release a new microservice to production. What would you check?

**Answer:**

I would check health endpoints, logging, metrics, alerts, security, capacity, and dependency handling. I would also verify CI/CD tests, rollback procedures, secrets management, and on-call documentation. For a critical service, I would expect load-test results and defined SLIs and SLOs. I would ask the team to address any critical gaps before release.

### Q7. Your service has consumed 90% of its monthly error budget in two weeks, but the product team wants to release new features. What would you do?

**Answer:**

I would explain the reliability risk using error-budget data and identify what caused the budget consumption. If the service is unstable, I would recommend pausing high-risk releases and prioritizing reliability fixes. Low-risk changes could continue with canary deployments and clear rollback criteria. I would make the decision based on our reliability policy and customer impact.

## 3. Incident Management and On-Call

### Q8. A deployment causes HTTP 500 errors for 40% of users. What would you do in the first 15 minutes?

**Answer:**

My first priority would be restoring service. I would confirm the impact, check deployment history and application logs, and notify the incident team. If the new release is responsible, I would roll back to the last known-good version. Then I would verify error rates and critical user journeys, communicate the recovery status, and investigate the root cause.

### Q9. Users report intermittent timeouts, but application logs show no obvious errors. How would you troubleshoot?

**Answer:**

I would trace requests across the load balancer, application, network, database, and external dependencies. I would check timeouts, connection resets, backend health, and connection pool metrics. Distributed tracing and request IDs would help identify where requests are getting stuck. Once I isolate the issue, I would mitigate it and add monitoring for the failure pattern.

### Q10. Database connections are exhausted during peak traffic. Restarting the application temporarily fixes it. What would you do?

**Answer:**

I would check active connections, pool utilization, long-running queries, and whether connections are being released properly. I would also calculate the total connection demand across all application replicas. Restarting only resets the connections, so I would fix the underlying leak or bottleneck, tune the pool settings, and load-test the solution.

### Q11. A firewall rule was accidentally removed, causing a 45-minute outage. How would you handle the post-incident review?

**Answer:**

I would reconstruct the timeline, identify the impact, and understand why the change was not caught earlier. I would focus on improving the process rather than blaming an individual. Actions might include Terraform plan reviews, automated policy checks, connectivity tests, and alerts for critical firewall changes. I would assign owners and track those actions to completion.

## 4. CI/CD and Infrastructure Automation

### Q12. Your CI/CD pipeline succeeds, but the application fails after deployment. How would you prevent this?

**Answer:**

I would review what the pipeline actually validates. A successful build doesn't guarantee that the deployed application works. I would add integration tests, configuration validation, post-deployment smoke tests, and health checks. For critical services, I would use canary deployment with automated monitoring and rollback when error rates or latency exceed defined thresholds.

### Q13. How would you deploy a high-traffic application without downtime?

**Answer:**

I would consider rolling, blue-green, or canary deployment depending on the application. For a critical service, I would consider a canary approach when the infrastructure supports it. I would gradually shift traffic, monitor errors and latency, and roll back if the new version causes problems. I would also ensure backward-compatible database changes and graceful shutdown.

### Q14. A Terraform change breaks production networking. How would you recover?

**Answer:**

I would identify which resources and network rules changed by reviewing the Terraform plan, apply logs, and actual infrastructure. I would restore the last known-good configuration through a controlled Terraform change and verify connectivity. I wouldn't blindly destroy resources or overwrite the state file. After recovery, I would improve plan reviews, policy checks, and connectivity testing.

### Q15. Your team manually restarts services during incidents. How would you automate this?

**Answer:**

I would start with a repetitive, well-understood recovery task. Using Python or Bash, I could check service health, collect diagnostic information, perform an approved restart, and verify recovery. I would include timeouts, retry limits, logging, and escalation if recovery fails. Destructive actions would require stronger safeguards or human approval.

## 5. Cloud, Microservices and Distributed Systems

### Q16. Your checkout API is slow, but the other microservices appear healthy. How would you troubleshoot?

**Answer:**

I would use distributed tracing to see how much time the checkout request spends in the payment, order, and inventory services. I would check database latency, dependency timeouts, retries, and connection pools. If a downstream service is slow, I would mitigate the impact using appropriate timeouts or circuit breakers. For payments, I would also ensure retries cannot create duplicate transactions.

### Q17. Traffic increases fivefold during a major event. Auto Scaling is enabled, but users still experience timeouts. What would you do?

**Answer:**

I would check whether the bottleneck is actually in the application tier. I would review load balancer metrics, scaling limits, database capacity, connection pools, cache hit ratio, and external API limits. Adding more application instances won't help if the database is already saturated. I would mitigate the immediate issue and improve capacity planning, caching, and load testing.

### Q18. Mobile and OTT users report buffering, but the website is healthy. How would you investigate?

**Answer:**

I would compare affected regions and devices, then check CDN latency, cache hit ratio, origin health, video segment delivery, and playback API errors. I would also investigate authentication and playback-session creation. Client-side telemetry would help distinguish buffering from API failures. After identifying the affected path, I would restore service and add alerts for playback startup failures and rebuffering.

## 6. Performance Testing and Reliability Engineering

### Q19. Your application works with 500 concurrent users but fails at 5,000. How would you troubleshoot it?

**Answer:**

I would use JMeter or k6 to increase the load gradually and identify when latency and errors start increasing. At the same time, I would check CPU, memory, database connections, query latency, and request queues. I would identify the saturated component, fix the bottleneck, and repeat the test. I would also confirm that the load generator itself isn't the limiting factor.

### Q20. Traffic is stable, but p95 latency increases from 300 ms to 2 seconds over several hours. There has been no deployment. What would you check?

**Answer:**

I would compare latency trends with memory usage, garbage collection, database connections, slow queries, and background job queues. I would also check downstream dependencies and infrastructure throttling. Gradually increasing latency could indicate a memory leak, connection leak, or growing backlog. I would mitigate customer impact, preserve diagnostic evidence, fix the root cause, and add alerts for early detection.