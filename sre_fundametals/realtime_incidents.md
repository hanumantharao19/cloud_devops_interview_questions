## What will you check if an application is slow but CPU and memory are normal?

- I will check disk I/O performance because high disk latency or I/O wait can slow the application even if CPU and memory are normal.

- I will verify network latency, packet loss, DNS resolution, and load balancer health since the application may depend on external services.

-  I will analyze database performance for slow queries, locks, or connection pool exhaustion, which are common causes of slowness.

- I will check application thread pools and database connection pool limits, as application-level bottlenecks can occur without high system usage.

- I will review application logs and error rates to identify timeouts, dependency failures, or external API delays.

-  Finally, I will verify if there were any recent deployments or configuration changes that might have introduced performance issues.

---
## How do you troubleshoot when everything looks healthy but users see errors?

1️⃣ Validate the Issue from User Perspective
- I will first try to reproduce the issue and check synthetic monitoring or real user monitoring (RUM) to confirm whether it is impacting all users or specific regions.

2️⃣ Check Application Logs for Hidden Errors
- Even if metrics look normal, there could be intermittent errors like 4xx/5xx responses, timeouts, or dependency failures visible in logs.

3️⃣ Check Load Balancer and Error Codes
- I will verify ALB/Nginx logs for 502, 503, 504 errors and check target group health or backend connectivity issues.

4️⃣ Verify Dependencies and External Services
- Sometimes everything looks healthy internally, but external APIs, databases, or third-party services may be failing or responding slowly.

5️⃣ Check Network, DNS, or CDN Issues
- There could be DNS resolution issues, SSL certificate problems, CDN caching issues, or regional network latency affecting users.

6️⃣ Check Recent Changes or Partial Rollouts
- I will verify if there was a recent deployment, config change, feature flag update, or canary release that might affect only some users.
---


## How do you approach a production issue step by step?

1️⃣ Acknowledge and Assess Impact

First, I acknowledge the alert and understand the impact — which service is affected, how many users are impacted, and the severity (P1, P2, etc.).

2️⃣ Stabilize the System (Immediate Mitigation)

Before deep investigation, I try to reduce impact by restarting services, scaling pods, rolling back recent deployments, or failing over if needed.

3️⃣ Check Monitoring and Logs

I check metrics like CPU, memory, disk, network, error rates, latency, and review application and system logs to identify anomalies.

4️⃣ Identify Recent Changes

Most production issues are caused by recent changes. I verify deployments, configuration changes, infrastructure updates, or feature flags.

5️⃣ Find Root Cause and Fix

After identifying the issue, I implement a proper fix — configuration correction, code rollback, scaling adjustment, dependency fix, etc.

6️⃣ Post-Incident Review (RCA)

After resolution, I document the root cause, timeline, impact, and preventive measures to avoid recurrence. If needed, I improve monitoring or alerts.
---

