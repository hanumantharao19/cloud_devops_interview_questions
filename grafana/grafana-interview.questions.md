## 1. What is Grafana?
- Grafana is an open-source visualization and monitoring platform that helps you create dashboards from data sources like Prometheus, Loki, InfluxDB, Elasticsearch, MySQL, etc.
---
## 2. What are Grafana dashboards?
- Dashboards are visual collections of panels (graphs, tables, alerts) used to monitor metrics and logs.
---
## 3. What are Grafana panels?
- Panels are the building blocks of dashboards—e.g., Graph, Gauge, Bar chart, Table, Heatmap.
---
## 4. What are some popular Grafana data sources?

- Grafana supports many data sources to visualize metrics and logs.

- Prometheus – Used for monitoring and visualizing system and application metrics.

- Loki – Used for log aggregation and log analysis.

- Elasticsearch – Used for searching and visualizing log and text-based data.

- InfluxDB – A time-series database used for metrics and performance data.

- Graphite – Used for storing and visualizing time-series metrics.

- AWS CloudWatch – Used to monitor AWS services and infrastructure.

- MySQL / PostgreSQL – Used to visualize data stored in relational databases.
---
## 5. Difference between Prometheus and Grafana?

- Prometheus collects and stores metrics; Grafana visualizes them.
---
## 6. What is Grafana Loki?

- Loki is a log aggregation system (like ELK), optimized for Kubernetes. It stores logs indexed by labels, not full text, making it cheaper.

## 7 How do you prevent users from editing production dashboards?

## Answer:
- I use folder-level permissions and make dashboards read-only for most users. Only a small admin group has edit access.
---
## 8 How do you troubleshoot Grafana alert not firing?

## Answer:
- I check alert evaluation interval, datasource connectivity, and test the query manually. I also verify notification channels and alert state history.
---
## 8. What’s the difference between using alerts in Grafana vs Prometheus Alertmanager?

## Answer:
- Prometheus Alertmanager is better for infrastructure alerts and reliability. Grafana alerts are useful for dashboard-level or business alerts. In production, Prometheus alerts are primary.
---
## 9 How do you version control Grafana dashboards?
 - Dashboards are exported as JSON and stored in Git. Changes go through pull requests and reviews, just like application code.
---
## 10. How can Grafana be secured in a production environment?

- Enable authentication using LDAP, OAuth, SSO, or cloud IAM.
- Use role-based access control (RBAC) to restrict dashboard and data source access.
- Always enable HTTPS/TLS to secure data in transit.
- Restrict data source permissions so users can access only what they need.
- Disable anonymous access in production environments.
- Regularly update Grafana to fix security vulnerabilities.
---

## 11 How do you reduce query load on Prometheus caused by Grafana?

## Answer:
- I use recording rules in Prometheus for expensive queries and query those metrics in Grafana. I also increase dashboard refresh intervals and avoid wide time ranges by default.
---
## 12. How does Grafana handle multi-tenancy?

- Using Folders, Teams, Permissions, and Organizations.

## 13. How do you scale Grafana?

-  Grafana is scaled mainly by running multiple Grafana instances behind a load balancer. 
- All instances share the same database (MySQL/PostgreSQL) and common storage for dashboards and users. 
- For high traffic, we also optimize dashboards and increase backend resources.
- Store dashboards in Git and deploy automatically

## 14. Difference between Grafana OSS, Grafana Enterprise, and Grafana Cloud?

## Grafana OSS (Open Source)

 - Free and self-hosted
 - Provides core dashboarding and visualization features
 - No official enterprise support

## Grafana Enterprise
  - Paid, self-hosted version
  - Includes advanced security features like enhanced RBAC, reporting, and audit logs
  - Comes with enterprise plugins and official support

## Grafana Cloud
- Fully managed SaaS offering
- No infrastructure to manage
- Includes hosted Grafana, Prometheus, Loki, Tempo, alerting, and long-term storage

## 15. Why does Grafana show “No Data” even when Prometheus has metrics

- Wrong time range selected
  - Grafana may be showing a time window where no data exists.

- Incorrect Prometheus query or metric name
   - A wrong PromQL query or typo in metric name results in no data.

- Label mismatch in the query
   - Using incorrect labels like job, instance, or namespace returns empty results.

- Prometheus target or scrape issue
   - If the target is down or scrape is failing, Grafana cannot display data.

## 16. How do you use labels effectively?

- Correct use of labels reduces cardinality and improves Loki performance.

## 17. Grafana dashboard is loading slowly. How do you troubleshoot it?

- Check the data source query
  - Slow PromQL / SQL queries are the most common cause
  - Reduce time range, use proper filters (job, namespace), and avoid heavy functions
- Reduce number of panels
  - Too many panels on a single dashboard slow down loading

- Check dashboard refresh interval
  - Very small refresh intervals (5s, 10s) increase load

- Review Prometheus performance
   - Check CPU, memory, and disk I/O of Prometheus

- Check Grafana server resources

  - Ensure Grafana has enough CPU and memory