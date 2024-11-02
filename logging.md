# Logging

Logging is crucial to being able to monitor, debug and analyze incidents.

Syslog is the standard unix system logging format,
but there are more advanced packages with search filtering and analysis on top these days.

<!-- INDEX_START -->

- [Summary](#summary)
- [Syslog](#syslog)
  - [Syslogd](#syslogd)
  - [Syslog-ng](#syslog-ng)
  - [RSyslog](#rsyslog)
- [Logging Platform Software](#logging-platform-software)
  - [ELK - Elasticsearch, Logstash, Kibana](#elk---elasticsearch-logstash-kibana)
  - [Graylog](#graylog)
  - [Loki](#loki)
  - [Prometheus](#prometheus)
- [Logging Agents](#logging-agents)
  - [LogStash](#logstash)
  - [Fluentd / Fluentbit](#fluentd--fluentbit)
  - [Filebeat](#filebeat)
  - [Vector](#vector)
- [Cloud Logging](#cloud-logging)
  - [Loggly](#loggly)
  - [SumoLogic](#sumologic)
  - [AWS Cloudwatch](#aws-cloudwatch)
  - [GCP Logging](#gcp-logging)
  - [Azure Monitor Logs](#azure-monitor-logs)
  - [Papertrail](#papertrail)
- [CEF - Common Event Format](#cef---common-event-format)

<!-- INDEX_END -->

## Summary

- **Syslog-ng** and **Rsyslog** are solid, mature solutions for large infrastructure logging
- **ELK Stack** and **Graylog** are great for full-scale log aggregation and search
- **Fluentd** and **Loki** are lightweight options ideal for cloud-native and Kubernetes environments
- **Prometheus** and **Vector** work well if you’re handling both logs and metrics together

## Syslog

The classic unix text based logging system which typically logs to the `/var/log/` directory.

Syslog can traditionally log to a remote syslog server on UDP port 514.

[Syslog-ng](syslog-ng.md) can log remotely over TCP 514 for reliability.

Common syslog logging daemons:

### Syslogd

The classic syslog daemon for unix system logging is simple to configure, but was outdated by the 2000s.

Consider using [Syslog-ng](syslog-ng.md) or RSyslog below instead.

### Syslog-ng

Excellent well-established next generation syslog daemon.

See [Syslog-ng](syslog-ng.md) doc.

### RSyslog

<https://www.rsyslog.com/>

'Rocket-fast syslog'

- Efficient for both small and large-scale environments
- Extremely customizable and supports multiple formats
- Good for distributed logging
  - supports [RELP](https://en.wikipedia.org/wiki/Reliable_Event_Logging_Protocol) to prevent remote logging message
    loss

I preferred the design quality of [Syslog-ng](syslog-ng.md).

## Logging Platform Software

### ELK - Elasticsearch, Logstash, Kibana

<https://www.elastic.co/elastic-stack>

- **Components**:
  - **Elasticsearch**: Stores and indexes logs
  - **Logstash**: Collects, parses, and enriches logs
  - **Kibana**: Visualizes logs in dashboards
- **Strengths**:
  - Excellent for real-time log analysis
  - Highly scalable and flexible
  - Strong visualization with Kibana
- **Use Cases**: Centralized logging for distributed systems, troubleshooting, and metrics

### Graylog

<https://graylog.org/>

- **Description**: Centralized log management system with enhanced search capabilities
- **Strengths**:
  - Built-in alerting and notifications
  - Supports structured and unstructured data
  - Scalable and easy-to-use UI
- **Use Cases**: Log aggregation and analysis, security auditing

### Loki

<https://grafana.com/oss/loki/>

- **Description**: Log aggregation system designed to work with [Grafana](grafana.md)
- **Strengths**:
  - Optimized for low cost and efficiency
  - Indexes metadata, not full logs, making it more lightweight
  - Ideal for environments where you already use [Prometheus](prometheus.md) and [Grafana](grafana.md)
- **Use Cases**: Lightweight logging in Kubernetes, cloud-native environments, and cost-effective log aggregation

### Prometheus

See [Prometheus](prometheus.md) doc.

- **Description**: Primarily used for monitoring and metrics, but it can also be used for logging
- **Strengths**:
  - Focus on metric collection with time-series databases
  - Integrates well with [Grafana](grafana.md) for visualization
  - Lightweight and efficient for real-time monitoring
- **Use Cases**: Infrastructure monitoring, microservices logging, and alerting

## Logging Agents

### LogStash

See [LogStash](logstash.md) doc.

### Fluentd / Fluentbit

See [Fluentd / Fluentbit](fluentd.md) doc.

### Filebeat

by Elastic.co of [Elasticsearch](elasticsearch.md) fame.

<https://www.elastic.co/beats/filebeat>

### Vector

<https://vector.dev/>

- **Description**: A high-performance observability data pipeline
- **Strengths**:
  - Focused on performance and efficiency
  - Can handle logs, metrics, and traces in one unified platform
  - Lightweight and flexible, with support for multiple sources and destinations
- **Use Cases**: Handling both logs and metrics, observability pipelines for distributed systems

## Cloud Logging

### Loggly

<https://www.loggly.com/>

- **Description**: Cloud-based log management platform that offers a free version
- **Strengths**:
  - Provides real-time log analysis with powerful search capabilities
  - Cloud-native with fast setup
  - Offers integrations with DevOps tools
- **Use Cases**: Centralized logging for DevOps, debugging, and troubleshooting

### SumoLogic

<https://www.sumologic.com/>

### AWS Cloudwatch

<https://aws.amazon.com/cloudwatch/>

### GCP Logging

<https://cloud.google.com/logging>>

### Azure Monitor Logs

<https://learn.microsoft.com/en-us/azure/azure-monitor/logs/data-platform-logs>

### Papertrail

<https://www.papertrail.com/>

- **Description**: A log aggregation and management system with a focus on simplicity
- **Strengths**:
  - Simple, fast, and reliable
  - Provides real-time log searching and alerts
- **Use Cases**: Log aggregation for small to medium-sized systems

## CEF - Common Event Format

- Syslog prefix of `<data> <host>`
  - can omit this if writing to file without Syslog, starting instead with just `CEF:version|...|...`
- pre-defined protocol + header fields for product / version with pipe separators
- suffix extension is `key=value` pairs
- UTF-8 encoded entire message
- pipes `|` must be escaped with backslash in header portion but not extension portion
- equal `=` must be escaped with backslash in extension portion but not header portion
- newlines must be encoded as `\r` or `\n` to keep it on one line

eg. from Implementing ArcSight Common Event Format pdf:

```log
Jan 18 11:07:53 host CEF:Version|Device Vendor|Device Product|Device Version|Device Event Class ID|Name|Severity|[Extension]
```

eg.

```log
Jan 18 11:07:53 host CEF:0|Security|threatmanager|1.0|100|worm successfully stopped|10|src=10.0.0.1 dst=2.1.2.2 spt=1232
```

**Ported from private Knowledge Base page 2012+** (should have kept notes in 2005+)**
