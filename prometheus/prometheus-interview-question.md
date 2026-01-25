## 1. What is Prometheus?

- Prometheus is an open-source monitoring and alerting tool used to collect, store, and monitor system and application metrics.
---
## 2 How does Prometheus work? Explain its architecture or workflow

- Applications and servers expose metrics in a format Prometheus understands

- Prometheus pulls (scrapes) these metrics at regular intervals

- Metrics are stored in a time-series database

- Data is queried using PromQL

- Alerts are triggered through Alertmanager when thresholds are crossed
---
## 3. What are the main components of Prometheus?

- Prometheus has the following main components:

## Prometheus Server

- The core component
- Scrapes metrics from targets, stores them in a time-series database, and evaluates rules

## Exporters

- Collect metrics from systems and applications
- Examples: Node Exporter (servers), Kubernetes exporter, MySQL exporter

## Client Libraries

- Used by applications to expose custom metrics
- Available for languages like Go, Python, Java

## Pushgateway

- Used for short-lived or batch jobs
- Allows jobs to push metrics to Prometheus

## Alertmanager
-  Handles alerts sent by Prometheus
- Sends notifications via email, Slack, PagerDuty, etc.

---

## 4. What port Prometheus runs on?

-  Default: 9090
---
## 5. What is a time-series database in Prometheus?

- A time-series database in Prometheus stores metric values along with timestamps, allowing monitoring and analysis of data over time.
---
## 6 What is PromQL and What Is Its Purpose?
- PromQL (Prometheus Query Language) is the query language used in Prometheus to read and analyze metrics stored in its time-series database.

- PromQL is used to:
## Fetch metrics
Get current or historical metric values
## Analyze performance
- Calculate averages, rates, and percentages
## Create alerts
- Define alert rules (e.g., CPU > 80% for 5 minutes)
## Build dashboards

- Used by Grafana to visualize metrics

---

## 7. What is Prometheus Alertmanager and why is it used?

- Receives alerts from Prometheus.

- Deduplicates: If multiple alerts are identical, it avoids sending duplicates.

- Groups alerts: Combines similar alerts into a single notification to avoid alert spam.

- Sends notifications to configured receivers like Slack, email, PagerDuty, or webhooks.

---
## 8. Difference between Prometheus and Grafana?

Prometheus collects and stores metrics.
Grafana visualizes metrics.

---
## 9. Prometheus shows NO DATA. What do you check?

- If Prometheus shows no data, check target status, metrics endpoint, scrape configuration, network access, and Prometheus logs.
---
## 10. High CPU usage in Prometheus — what could be the reason?

- High CPU usage in Prometheus is usually caused by too many metrics(targets), short scrape intervals, expensive queries(long quries), or long data retention
---
## 11.Alerts are not firing in Prometheus — what should you check?
- If alerts are not firing, check alert rule syntax, expression correctness, rule loading, target health, and Alertmanager configuration.
---
## 12 How does Prometheus store data? Does it use a database or EBS volume?
- Prometheus stores metrics in its own built-in time-series database on local disk or a persistent volume; it does not use an external database

## In Kubernetes:
- Prometheus stores data on a Persistent Volume (PV)

- This PV can be backed by:
   - EBS (AWS)
   - Persistent Disk (GCP)
   - Azure Disk
   - NFS
---
## 13. How to create recording rules?

Used to precompute heavy queries and improve performance.

groups:
- name: example
  rules:
  - record: job:http_in_progress:sum
    expr: sum by (job) (http_in_progress_requests)

🔹 Prometheus in Kubernetes Questions

## 14 what is significance  of the job label in prometheus targets
- The job label are used to groups related targets in Prometheus and helps in querying, aggregating, and organizing metrics efficiently.
## 15 What are the commonly used exporters in Prometheus and why are they used?

- Prometheus does not collect metrics directly from all systems, so it uses exporters—small applications that expose metrics in a format Prometheus understands. Commonly used exporters include:

## Node Exporter
- Collects system-level metrics from Linux servers
- CPU, memory, disk, network usage

## cAdvisor / kube-state-metrics
- Collects container and Kubernetes metrics
- Pod CPU/memory usage, deployment status, node health

## MySQL / PostgreSQL Exporter
- Collects database metrics
- Query performance, connections, cache hits

## Blackbox Exporter

- Monitors external services via HTTP, DNS, TCP, ICMP
- Checks website availability or latency

## Pushgateway

- Used for short-lived jobs to push metrics to Prometheus
---
## 16 What are the commonly used Prometheus functions, and when do we use them?
Prometheus provides functions in PromQL to process and analyze metrics
- rate() / irate() – Calculate per-second rate of counters for metrics like HTTP requests.
- increase() – Shows total increase of a counter over a time period.
- sum() / avg() – Aggregate metrics across instances or calculate average values.
- histogram_quantile() – Compute percentiles (e.g., 95th percentile response time) from histogram metrics.
```
histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m]))
```
---
## 17 What is the difference between Prometheus pull vs push model?

- Pull: Prometheus scrapes metrics from endpoints (default, most common)
- Push: Short-lived jobs push metrics to Pushgateway (used for ephemeral jobs)

---
## 18 How do you handle long-term storage in Prometheus?
- Prometheus stores data locally by default, which is fast but not suitable for long-term retention or very large-scale metrics.

- Thanos, Cortex, and VictoriaMetrics are additional software tools that integrate with Prometheus to provide long-term, scalable storage.

- These tools store Prometheus metrics in object storage like S3 (AWS), GCS (Google Cloud), or Azure Blob, and also support high availability and global querying.

---
## 19 What is the difference between Node Exporter and kube-state-metrics?

- Node Exporter provides host-level system metrics (CPU, memory, disk), while kube-state-metrics provides Kubernetes object-level metrics like Deployments, Pods, and ReplicaSets status.

---
## 20 What types of metrics are available in Prometheus and what are their purposes?

## Counter

A metric that only increases over time
Used for counting events like HTTP requests, errors, or jobs completed
Example: http_requests_total

## Gauge

- A metric that can go up or down
- Used for values that fluctuate like CPU usage, memory, or queue size
- Example: node_memory_Active_bytes

## Histogram

- Measures distributions of events over defined buckets
- Used for latency, request duration, or response sizes
- Example: http_request_duration_seconds_bucket

## Summary

- Similar to histogram but calculates quantiles like 50th, 95th percentile
- Used for tracking request durations or latency percentiles
- Example: http_request_duration_seconds