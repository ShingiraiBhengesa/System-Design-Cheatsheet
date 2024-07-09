<h1 align="center">The System Design Cheat Sheet</h1>
<p align="center">
<img src="https://img.shields.io/github/last-commit/bhavul/system-design-cheatsheet"/>
<a href="https://github.com/gavr-dev/system-design-cheat-sheet/blob/main/LICENSE" alt="GPLv3 licensed"><img src="https://img.shields.io/badge/license-GPLv3-blue"/></a><br>
  <a href="https://www.buymeacoffee.com/bhavul" target="_blank"><img src="https://img.shields.io/badge/-buy_me_a%C2%A0coffee-gray?logo=buy-me-a-coffee" alt="Buy Me A Coffee"></a>
  <br>
  System Design Studying can be daunting. It can be useful to have a table to know what problems requires what components, and for those components what caveats they bring and how to mitigate them. This repository gives you a table to serve just this purpose.
</p>

----

<p align="center"> Your ⭐ on the repo would bring me joy, validate the effort and motivate me to do more like this. ✨ </p>

----

| Use Cases/Problems                                                                                                                 | System Design Questions                                                                                     | ⭐ Component                      | What it solves                                                  | Caveats/Issues                                      | Mitigations                                                                                                                                        | Examples of Tools                           |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------- | ----------------------------------------------------------- | --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| \- Unified API access: Centralizes client requests.<br>\- Security: Manages authentication and authorization.                      | \- Design an API gateway for microservices.<br>\- Implement secure and scalable API access.                | **API Gateway**                     | Single entry point, manages authentication and routing.     | Can become a bottleneck, adds latency.              | \- Use multiple gateways with load balancing.<br>\- Implement rate limiting and caching.<br>\- Use circuit breakers and retries.                   | Kong, Apigee, AWS API Gateway               |
| \- High traffic websites: Ensures uptime and balances load.<br>\- Scalable APIs: Distributes incoming requests.                    | \- Design a scalable web application.<br>\- Build a highly available online service.                       | **Load Balancer** across multiple redundant workers                   | Distributes traffic across workers, improves reliability and availability. | Single point of failure, adds complexity.           | \- Use multiple load balancers in different regions.<br>\- Implement health checks.<br>\- Use DNS-based load balancing.                            | Nginx, HAProxy, AWS ELB                     |
| \- Financial transactions: Requires ACID compliance.<br>\- Complex queries: Needs structured and relational data.                  | \- Design a financial transaction system.<br>\- Create a scalable relational database.                     | **SQL Database**                    | Strong ACID properties, structured data, complex queries.   | Limited scalability, schema management.             | \- Implement sharding.<br>\- Use read replicas.<br>\- Employ clustering and partitioning.                                                          | MySQL, PostgreSQL, MS SQL Server            |
| \- Large-scale data: Supports horizontal scaling.<br>\- Unstructured data: Flexible schema adapts to changes.                      | \- Design a large-scale user profile store.<br>\- Create a scalable data storage solution.                 | **NoSQL Database**                  | Flexible schema, horizontal scalability, high performance.  | Eventual consistency, limited transaction support.  | \- Use consistency settings (e.g., quorum reads/writes).<br>\- Design for idempotent operations.<br>\- Implement conflict resolution strategies.   | MongoDB, Cassandra, DynamoDB                |
| \- High availability: Ensures data is replicated and available. | \- Design a data replication strategy.<br>\- Implement a highly available database system.                 | **Data Replication**             | Ensures data durability, to ensure system availability.                   | Increases costs, consistency issues.                | \- Use asynchronous replication.<br>\- Implement conflict resolution.<br>\- Use multi-master replication.                                          | AWS RDS standby (synchronous), AWS RDS Read Replicas (asynchronous), MongoDB Replica Set (asynchronous)|
| \- High read load: Reduces latency for frequent reads.<br>\- Session storage: Speeds up access to session data.                    | \- Design a high-performance caching layer.<br>\- Optimize read-heavy workload.                            | **Cache**                           | Reduces latency, decreases load on databases.               | Cache consistency issues, potential for stale data. | \- Implement cache invalidation strategies.<br>\- Use Time-to-Live (TTL) settings.<br>\- Employ write-through or write-back caching.               | Redis, Memcached                            |
| \- Real-time analytics: Requires fast data access.<br>\- Leaderboards: High-speed data retrieval is crucial.                       | \- Design a real-time analytics system.<br>\- Create a fast leaderboard service.                           | **In-Memory Database**              | Extremely fast data retrieval, reduces latency.             | Volatile storage, high memory cost.                 | \- Enable persistence options.<br>\- Use hybrid storage models (in-memory + disk).<br>\- Implement data backup strategies.                         | Redis, Memcached                            |
| \- Event streaming: Manages high-throughput data streams.<br>\- Real-time processing: Facilitates real-time data flows.            | \- Design a real-time event streaming platform.<br>\- Implement a reliable messaging system.               | **Message Broker**                  | Facilitates message exchange, supports multiple patterns.   | Bottleneck potential, delivery guarantees.          | \- Use scalable brokers with partitions.<br>\- Implement backpressure handling.<br>\- Monitor message broker performance.                          | Apache Kafka, RabbitMQ, ActiveMQ            |
| \- Event-driven systems: Manages asynchronous events.<br>\- Microservices: Decouples service communication.                        | \- Design an event-driven architecture.<br>\- Create a reliable task processing system.                    | **Distributed Queue**               | Manages asynchronous communication, decouples components.   | Message ordering and delivery guarantees.           | \- Use message brokers with strong ordering guarantees.<br>\- Implement idempotent message processing.<br>\- Use message deduplication techniques. | Apache Kafka, RabbitMQ, AWS SQS             |
| \- Large applications: Enhances modularity and scalability.<br>\- Continuous delivery: Facilitates independent deployment.         | \- Design a scalable microservices architecture.<br>\- Build a modular, independently deployable system.   | **Microservices**                   | Improves modularity, independent deployment.                | Increased communication complexity.                 | \- Use service meshes.<br>\- Implement standardized APIs.<br>\- Use centralized logging and monitoring.                                            | Docker, Kubernetes, Istio                   |
| \- Microservices: Enables service discovery.<br>\- Dynamic environments: Tracks changing service instances.                        | \- Design a service discovery mechanism.<br>\- Implement dynamic service registration.                     | **Service Registry**                | Tracks services and their instances.                        | High availability required, consistency issues.     | \- Use distributed service registries.<br>\- Implement regular health checks.<br>\- Use consensus algorithms for consistency.                      | Consul, Eureka, Zookeeper                   |
| \- Content-heavy sites: Improves load times for users.<br>\- Global reach: Distributes content across regions.                     | \- Design a content delivery system.<br>\- Optimize a global website’s performance.                        | **CDN (Content Delivery Network)**  | Reduces latency, improves load times.                       | Cache invalidation complexity, cost.                | \- Implement cache purging strategies.<br>\- Use regional CDNs.<br>\- Monitor CDN performance and hit rates.                                       | Cloudflare, Akamai, AWS CloudFront          |
| \- Business intelligence: Centralizes analytics data.<br>\- Historical analysis: Supports complex querying over large datasets.    | \- Design a data warehouse for analytics.<br>\- Build a scalable business intelligence platform.           | **Data Warehouse**                  | Centralizes data, supports complex queries.                 | High storage and maintenance costs.                 | \- Use data compression and partitioning.<br>\- Implement data lifecycle management.<br>\- Use cloud-based, scalable data warehouses.              | Amazon Redshift, Snowflake, Google BigQuery |
| \- E-commerce sites: Provides fast product search.<br>\- Large datasets: Enables full-text search over extensive data.             | \- Design a product search system.<br>\- Implement a scalable search solution.                             | **Search Engine**                   | Enables fast search over large datasets.                    | Indexing and maintenance required.                  | \- Implement efficient indexing strategies.<br>\- Use distributed search architectures.<br>\- Optimize search queries and relevance.               | Elasticsearch, Solr, Algolia                |
| \- Media storage: Handles large files like images and videos.<br>\- Backup solutions: Stores and retrieves backups.                | \- Design a scalable file storage system.<br>\- Implement a reliable backup solution.                      | **File Storage**                    | Scales with data growth, handles unstructured data.         | Backup and redundancy required, retrieval latency.  | \- Use distributed file systems.<br>\- Implement multi-region replication.<br>\- Use lifecycle policies for data management.                       | AWS S3, Google Cloud Storage, HDFS          |
| \- Data warehousing: Prepares data for analysis.<br>\- Data migration: Transforms data from multiple sources.                      | \- Design an ETL pipeline for a data warehouse.<br>\- Build a reliable data integration system.            | **ETL Pipeline**                    | Facilitates data integration and analysis.                  | Complex to build and maintain.                      | \- Use managed ETL services.<br>\- Implement monitoring and error handling.<br>\- Use data validation and transformation tools.                    | Apache Nifi, AWS Glue, Talend               |
| \- System reliability: Monitors uptime and performance.<br>\- Issue detection: Alerts for anomalies and failures.                  | \- Design a system monitoring solution.<br>\- Implement an alerting and dashboard system.                  | **Monitoring System**               | Tracks system health, enables alerting.                     | High overhead, potential noise.                     | \- Use threshold tuning and anomaly detection.<br>\- Implement efficient data collection.<br>\- Use centralized monitoring dashboards.             | Prometheus, Grafana, Datadog                |
| \- Debugging: Captures logs for issue diagnosis.<br>\- Compliance: Maintains audit trails.                                         | \- Design a centralized logging system.<br>\- Implement a scalable logging and analysis solution.          | **Logging System**                  | Aids in auditing and troubleshooting.                       | Large data volumes, storage and querying.           | \- Use log rotation and retention policies.<br>\- Implement centralized logging.<br>\- Optimize log storage and indexing.                          | ELK Stack, Splunk, Fluentd                  |
| \- Secure applications: Manages user identity and access.<br>\- Single sign-on: Centralizes authentication across services.        | \- Design a secure authentication system.<br>\- Implement a single sign-on solution.                       | **Authentication Service**          | Enhances security, manages user authentication.             | Single point of failure, security measures needed.  | \- Use multi-factor authentication.<br>\- Implement redundancy and failover.<br>\- Use secure token storage and management.                        | OAuth, Okta, Auth0                          |
| \- Containerized apps: Automates container management.<br>\- Microservices: Coordinates service deployments.                       | \- Design a container orchestration system.<br>\- Implement a CI/CD pipeline for microservices.            | **Orchestration Tool**              | Automates deployment and management.                        | Adds complexity, learning curve.                    | \- Use managed orchestration services.<br>\- Implement robust CI/CD pipelines.<br>\- Use monitoring and scaling tools.                             | Kubernetes, Docker Swarm, Mesos             |
| \- Dynamic applications: Centralizes config changes.<br>\- Large systems: Manages configurations across services.                  | \- Design a configuration management system.<br>\- Implement dynamic configuration updates.                | **Configuration Service**           | Centralizes configuration management.                       | Single point of failure, secure access needed.      | \- Use distributed configuration stores.<br>\- Implement encryption for sensitive data.<br>\- Use versioning and rollback mechanisms.              | Consul, etcd, Spring Cloud Config           |
| \- Real-time dashboards: Aggregates live data feeds.<br>\- Monitoring: Provides instant insights from data streams.                | \- Design a real-time analytics system.<br>\- Implement a live data aggregation platform.                  | **Real-Time Data Aggregation**      | Enables real-time analytics and monitoring.                 | High complexity, data velocity issues.              | \- Use stream processing frameworks.<br>\- Implement windowing and aggregation techniques.<br>\- Monitor and scale processing infrastructure.      | Apache Flink, Apache Storm, AWS Kinesis     |
| \- Microservices: Tracks requests across services.<br>\- Performance tuning: Identifies bottlenecks and delays.                    | \- Design a distributed tracing system.<br>\- Implement performance monitoring for microservices.          | **Distributed Tracing**             | Aids in debugging and performance monitoring.               | High overhead, integration required.                | \- Use sampling to reduce overhead.<br>\- Implement efficient trace storage.<br>\- Use correlation IDs for request tracking.                       | Jaeger, Zipkin, OpenTracing                 |
| \- Fault tolerance: Prevents system overloads.<br>\- Resilient services: Isolates failures in microservices.                       | \- Design a fault-tolerant microservices system.<br>\- Implement circuit breakers for service reliability. | **Circuit Breaker**                 | Protects services from cascading failures.                  | Adds complexity, tuning needed.                     | \- Use monitoring tools to detect failures.<br>\- Implement fallback strategies.<br>\- Use retries and exponential backoff.                        | Hystrix, Resilience4j, Istio                |
| \- API management: Protects against request floods.<br>\- Fair resource allocation: Ensures fair usage policies.                   | \- Design an API rate limiting system.<br>\- Implement a fair resource allocation mechanism.               | **Rate Limiter**                    | Controls request rate, prevents abuse.                      | Can impact user experience.                         | \- Use dynamic rate limiting.<br>\- Implement user-based quotas.<br>\- Use monitoring to adjust limits.                                            | Kong, Envoy, Nginx                          |
| \- Periodic tasks: Automates recurring jobs.<br>\- Batch processing: Manages large data processing tasks.                          | \- Design a job scheduling system.<br>\- Implement a reliable task processing system.                      | **Scheduler**                       | Manages background jobs and tasks.                          | Requires monitoring, can become bottleneck.         | \- Use distributed schedulers.<br>\- Implement job prioritization.<br>\- Use monitoring and retry mechanisms.                                      | Apache Airflow, Celery, Kubernetes CronJobs |
| \- Microservices: Handles inter-service communication.<br>\- Observability: Provides insights into service interactions.           | \- Design a service mesh for microservices.<br>\- Implement observability for service interactions.        | **Service Mesh**                    | Manages microservices communication.                        | Adds operational complexity.                        | \- Use managed service meshes.<br>\- Implement automation tools.<br>\- Use monitoring and observability tools.                                     | Istio, Linkerd, Consul Connect              |
| \- Disaster recovery: Ensures data is safe and recoverable.<br>\- Data integrity: Maintains backups for compliance.                | \- Design a backup and recovery system.<br>\- Implement a reliable disaster recovery solution.             | **Data Backup and Recovery**             | Ensures data durability, protects against data loss.        | Resource-intensive, regular testing needed.  Increases costs.  if backups are not up to date there will be data loss. Backup may not be accessible.       | \- Use automated backup solutions.<br>\- Implement multi-region storage.<br>\- Regularly test backup and recovery processes.                       | Use native backup capabilites of the data store, or centralized backup products like AWS Backup, Google Cloud Backup, Veeam      |
| \- Social networks: Models complex relationships.<br>\- Recommendation engines: Analyzes connected data.                           | \- Design a social network graph database.<br>\- Implement a recommendation engine.                        | **Graph Database**                  | Efficiently handles graph-based data and relationships.     | Steep learning curve, non-graph query inefficiency. | \- Use graph-specific optimizations.<br>\- Implement hybrid models for different data types.<br>\- Use indexing and caching for performance.       | Neo4j, Amazon Neptune, OrientDB             |
| \- Big data analytics: Stores and processes vast data.<br>\- Data warehousing: Prepares raw data for analytics.                    | \- Design a big data analytics platform.<br>\- Implement a data lake for diverse data types.               | **Data Lake**                       | Supports diverse data types and analytics.                  | Governance required, risk of becoming data swamp.   | \- Use metadata management.<br>\- Implement data cataloging.<br>\- Use data lifecycle policies.                                                    | AWS Lake Formation, Azure Data Lake, Hadoop |
| \- Event-driven architectures: Processes data streams in real-time.<br>\- Analytics: Real-time insights from continuous data flow. | \- Design a real-time data streaming system.<br>\- Implement an event-driven architecture.                 | **Data Streaming Platform**         | Facilitates real-time data processing.                      | High operational complexity.                        | \- Use managed streaming services.<br>\- Implement scaling strategies.<br>\- Monitor and optimize processing.                                      | Apache Kafka, AWS Kinesis, Google Pub/Sub   |


## Other tips
- Memorize non-functional requirements and be quick at back of the envelope calculations. [Use this link](https://gist.github.com/mwakaba2/8ad25dda8c71fe529855994c70743733). QPS and Storage numbers are often more important than others. To arrive at QPS, go from DAU for Product -> DAU for feature -> Read/Write -> Seconds in the day -> QPS.
- Going for L4/E4/Intermediate role: Feel free to ask as many Qs to interviewer as you want. Going for L5/E5/Senior role: Lead the interview, make choices yourself, and provide justifications and just 'confirm' with interviewer you're on the right track.
- First provide a high level design overview with all components you would have, then deep dive into each component and why it is useful, what are its pros and cons.

## Contributions

Community contributions both for issues and PRs are welcome. 

## Found it useful?
Thanks. :) Feel free to leave a star on the repo, or if you can afford it, <a href="https://www.buymeacoffee.com/bhavul" target="_blank"><img src="https://img.shields.io/badge/-buy_me_a%C2%A0coffee-gray?logo=buy-me-a-coffee" alt="Buy Me A Coffee"></a>.

Feel free to connect to stay updated. 
- LinkedIn : [![Linkedin: bhavul](https://img.shields.io/badge/-bhavul-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/bhavul/)](https://www.linkedin.com/in/bhavul/)
- X : [![Twitter Follow](https://img.shields.io/twitter/follow/bhavulgauri.svg?style=social)](http://twitter.com/bhavulgauri)
