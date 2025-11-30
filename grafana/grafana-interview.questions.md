## 1. What is Grafana?

Grafana is an open-source visualization and monitoring platform that helps you create dashboards from data sources like Prometheus, Loki, InfluxDB, Elasticsearch, MySQL, etc.

## 2. What are Grafana dashboards?

Dashboards are visual collections of panels (graphs, tables, alerts) used to monitor metrics and logs.

## 3. What are Grafana panels?

Panels are the building blocks of dashboards—e.g., Graph, Gauge, Bar chart, Table, Heatmap.

## 4. What are some popular Grafana data sources?

Prometheus

Loki

ElasticSearch

InfluxDB

Graphite

MySQL / PostgreSQL

AWS CloudWatch

Azure Monitor

## 5. Difference between Prometheus and Grafana?

Prometheus collects and stores metrics; Grafana visualizes them.

🔹 Intermediate Level
## 6. What is Grafana Loki?

Loki is a log aggregation system (like ELK), optimized for Kubernetes. It stores logs indexed by labels, not full text, making it cheaper.

## 7. How do you create alerts in Grafana?

Using Alert Rules, Contact Points, and Notification Policies. Alerts can be sent via:

Slack

Email

PagerDuty

Webhook

Teams

## 8. How do you secure Grafana?

Enable authentication (OAuth, LDAP, SSO)

Enable TLS/HTTPS

Use role-based access control (RBAC)

Folder-level permissions

Data source permission locking

## 9. What is Grafana Tempo?

Tempo is a distributed tracing backend compatible with OpenTelemetry, Jaeger, Zipkin.

## 10. How does Grafana support templating?

Using variables that allow dynamic dashboards. E.g., dropdown for environment, cluster, namespace.


## 11. How does Grafana handle multi-tenancy?

Using Folders, Teams, Permissions, and Organizations.

## 12. How do you scale Grafana?

Use Grafana Enterprise or Grafana Cloud

Use external database (MySQL/PostgreSQL)

Use a load balancer

Store dashboards in Git and deploy automatically

## 13. How do you integrate Grafana with Kubernetes?

Connect Prometheus (scraping kube-state-metrics)

Use Helm chart (grafana/grafana)

Use sidecar for dashboards

Use Loki for logs

Use Tempo for tracing

## 14. Difference between Grafana OSS, Grafana Enterprise, and Grafana Cloud?
Version	Features
OSS	Free, basic dashboards and alerts
Enterprise	RBAC, enterprise plugins, audit logs
Cloud	Fully managed SaaS with Prometheus, Loki, Tempo
## 15. What is annotation in Grafana?

Annotations mark events on graphs (deployments, failures, restarts).


## 16. How do you write PromQL for Grafana?

Example: CPU usage

rate(container_cpu_usage_seconds_total[5m])

## 17. Why does Grafana show "No Data" when Prometheus has metrics?

Common reasons:

Wrong PromQL query

Wrong labels

Incorrect time range

Data source misconfigured

## 18. How do you use labels effectively?

Correct use of labels reduces cardinality and improves Loki performance.

## 19. How do you backup Grafana?

Backup:

/var/lib/grafana (SQLite or data files)

grafana.ini

Dashboards (JSON export or Git)

## 20. How to automate dashboard deployment?

Using:

Grafana provisioning folders

ConfigMaps in Kubernetes

Terraform Grafana provider


## 21. Your Grafana dashboard loads slowly—how do you troubleshoot?

Heavy PromQL queries

Too many panels per dashboard

High cardinality metrics

Slow data source (Elastic, SQL)

Server resource issues

## 22. Alert is not firing in Grafana—what do you check?

Query returns data

Alert rule enabled

Evaluation interval

Contact point configured

## 23. Logs not appearing in Grafana Loki—how to debug?

Check Loki distributor

Verify promtail config

Validate labels

Check ingestion rate limit