---
tags:
  - monitoring
  - logging
date: 2025-03-19
---
# ELK Stack
Elasticsearch + Logstash + Kibana

> [!question]+ Is the ELK Stack Open Source?
> The ELK (Elasticsearch, Logstash, Kibana) Stack is not fully open source anymore. In 2021, Elastic changed its licensing model:
> 
> - Elasticsearch and Kibana moved from Apache 2.0 to a dual license:
>     - Elastic License 2.0 (non-open source)
>     - Server Side Public License (SSPL)
> 
> Neither license is considered open source by the Open Source Initiative. The SSPL restricts service providers from offering the software as a service without contributing back or purchasing a license.
> 
> Open source alternatives exist:
> 
> - OpenSearch (AWS fork of Elasticsearch)
> - OpenDistro (maintained by AWS)
> 
> Logstash remains Apache 2.0 licensed.

## Bullet Notes

- Beats → Data collection agents which forward data/logs to Logstash
- Logstash → Data input / filter / process / output → forward to another location
- Elasticsearch → query logstash data
- Kibana → Web-based front-end data visualization.

## Kibana

### Querying Data

- Kibana Supports 2 Query Languages:
	1. **Kibana Query Language (KQL)**
	2. **Lucene Query Language**