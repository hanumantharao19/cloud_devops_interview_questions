## 1. What is Prometheus?

Prometheus is an open-source monitoring and alerting system designed for metrics-based monitoring.
It uses:

Pull-based scraping

Multi-dimensional data model (labels)

PromQL query language

## 2. What are the main components of Prometheus?

Prometheus Server – scrapes & stores metrics

Exporter – exposes metrics (Node Exporter, cAdvisor, etc.)

Alertmanager – sends alerts

Pushgateway – for short-lived jobs

Service Discovery – Kubernetes, EC2, Consul

## 3. What port Prometheus runs on?

Default: 9090

## 4. What is a metric?

A numerical value representing a system state, like:

CPU usage

Memory

Pod restarts

Request latency

## 5. What is a time-series in Prometheus?

A metric tracked over time, stored with:

Metric name

Labels

Timestamp

Value


## 6. Explain PromQL.

PromQL is Prometheus' query language used to:

filter

aggregate

group

compute rates

Example:

rate(http_requests_total[5m])

## 7. Types of metrics in Prometheus?

Counter – only increases (requests, errors)

Gauge – increase/decrease (memory, temperature)

Histogram – bucketed samples (latency)

Summary – quantiles

## 8. Difference between Histogram and Summary?
Histogram	Summary
Aggregatable across instances	Not aggregatable
Stores buckets	Calculates quantiles
Good for dashboards	Good for client-side computation
## 9. What is Service Discovery in Prometheus?

Dynamic discovery of targets:

Kubernetes

EC2

Consul

DNS

Prometheus automatically updates targets without restarting.

## 10. What is a scrape interval?

How often Prometheus collects metrics.

Example:

scrape_interval: 15s

## 11. What is Label in Prometheus?

Key-value pairs for metric filtering.
Example:

node_cpu_seconds_total{mode="idle", cpu="0"}

## 12. What is Label Cardinality?

The number of possible combinations of labels.

⚠️ High cardinality = Prometheus becomes slow.
Examples:

user_id

transaction_id

pod_uid

## 13. What is AlertManager?

Component that:

Receives alerts from Prometheus

Groups alerts

Deduplicates

Sends notifications (Slack, email, PagerDuty, Webhook)

## 14. Difference between Prometheus and Grafana?

Prometheus collects and stores metrics.
Grafana visualizes metrics.

## 15. What is federation in Prometheus?

Federation = scrapping another Prometheus server.
Used for:

HA

Multi-cluster setup

Global metrics aggregation

## 16. How to scale Prometheus?

Prometheus is single-node, so scale using:

Thanos

Cortex

Mimir

These add:

Long-term storage

Multi-tenancy

Horizontal scaling

## 17. What is Thanos?

A project that adds:

Object storage (S3/GCS)

Query across Prometheus instances

Global dashboards

## 18. What is Pushgateway?

Used when metrics cannot be scraped:

Cron jobs

Short-lived scripts

Prometheus normally pulls, Pushgateway pushes.

## 19. How does Prometheus store data?

Time-series stored in:

TSDB blocks (2 hours)

WAL (Write Ahead Log)

## 20. What is "rate" and "irate" in PromQL?

rate()

Slow, smoothed average

Used for dashboards

irate()

Fast, instant rate

Used for alerts

Example:

rate(node_cpu_seconds_total[5m])

## 21. Prometheus shows NO DATA. What do you check?

Exporter is running

Target is up

Correct port

Firewall rules

Metrics endpoint reachable

Wrong PromQL query

Scrape interval too long

## 22. High CPU usage in Prometheus — what could be the reason?

High cardinality metrics

Too many targets

Huge PromQL queries

Very short scrape interval

## 23. Alerts are not firing — what do you check?

Alert rule is valid

Query returns data

Evaluate interval

AlertManager reachable

Time window correctness

Example mistake:

for: 1m


but scrape_interval is 2m.

## 24. How to avoid high cardinality?

Avoid labels like uuid, email, session_id

Limit pod-level labels

Avoid metrics per request

## 25. You need to monitor microservices in Kubernetes — what exporters do you use?

kube-state-metrics

cAdvisor

Node Exporter

Application metrics (client libraries)

Ingress metrics

## 26. Prometheus uses 100GB of storage — what do you do?

Increase retention only if required

Move to long-term store (Thanos, Mimir)

Reduce scrape interval

Reduce unnecessary labels

Delete unused metrics

## 27. How to create recording rules?

Used to precompute heavy queries and improve performance.

groups:
- name: example
  rules:
  - record: job:http_in_progress:sum
    expr: sum by (job) (http_in_progress_requests)

🔹 Prometheus in Kubernetes Questions
## 28. How does Prometheus discover pods in Kubernetes?

Using:

kubernetes_sd_config


Prometheus automatically finds:

Nodes

Pods

Services

Endpoints

## 29. What is kube-state-metrics?

Exporter that gives cluster state metrics:

Deployments

Pods

Nodes

PersistentVolumes

## 30. What is cAdvisor?

Container-level metrics:

CPU

Memory

I/O

Restarts