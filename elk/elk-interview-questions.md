ELK Stack (Elasticsearch, Logstash, Kibana)
- elasticsearch – Search engine for logging and data analytics
- curl -XGET
'localhost:9200/_cluster/health?pretty' – Get
cluster health status
- logstash – Server-side data processing pipeline
- logstash -f <config_file> – Run Logstash with the
specified configuration file
- kibana – Web interface for visualizing Elasticsearch data
- Kibana is generally accessed through a web browser
(http://localhost:5601)
