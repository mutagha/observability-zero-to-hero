
# 📚 7-Day Observability Tutorial Series

Welcome to the 7-Day Observability Tutorial Series! This repository contains the code and detailed explanations for setting up and understanding observability in Kubernetes using Prometheus, Grafana, Elasticsearch Fluentbit, Kibana, Jaeger, groundcover(eBPF), opentelemetry e.t.c.,.

## 📅 Overview of Each Day

### Day 1: Introduction to Observability
- **Concepts Covered**:
  - Introduction to Observability, Monitoring, Logging, and Tracing.
  - The difference between Monitoring and Observability.
  - Tools available for Monitoring and Observability.
  - Comparison between monitoring and observing in Bare-Metal Servers vs. Kubernetes.
- **Key Learning**:
  - Understand the fundamental concepts of observability.
  - Learn why monitoring and observability are crucial in modern IT environments.

### Day 2: Prometheus - Setting Up Monitoring
- **Concepts Covered**:
  - Introduction to Prometheus and its architecture.
  - Setup and configuration of Prometheus in an EKS cluster.
  - Installation of kube-prometheus-stack with Helm and integrating it with Grafana.
  - Basic queries and setup for monitoring with Prometheus and Grafana.
- **Key Learning**:
  - Get hands-on experience with Prometheus and Grafana.
  - Learn to install and configure Prometheus on Kubernetes.

### Day 3: Metrics and PromQL in Prometheus
- **Concepts Covered**:
  - Introduction to PromQL and basic querying techniques.
  - Aggregation and functions in PromQL to analyze metrics data.
- **Key Learning**:
  - Master the Prometheus Query Language (PromQL) for querying and analyzing metrics.

### Day 4: Instrumentation and Custom Metrics
- **Concepts Covered**:
  - Instrumentation for adding monitoring capabilities to applications.
  - Understanding different types of metrics in Prometheus: Counter, Gauge, Histogram, and Summary.
  - Writing custom metrics in a Node.js application using the `prom-client` library.
  - Dockerizing the application and deploying it on Kubernetes.
  - Setting up Alertmanager for alerting based on custom metrics.
- **Key Learning**:
  - Learn how to instrument applications to expose custom metrics.
  - Configure alerts in Alertmanager to monitor application performance.
  - Understand how to work with different types of metrics in Prometheus.

### Day 5: Logging with EFK Stack
- **Concepts Covered**:
  - Introduction to logging in distributed systems and Kubernetes.
  - Setting up the EFK stack (Elasticsearch, Fluentbit, Kibana) on Kubernetes.
  - Detailed setup and configuration for collecting and visualizing logs.
  - Cleaning up the Kubernetes cluster and resources.
- **Key Learning**:
  - Understand the importance of logging and how to set up

### Day 6: Distributed Tracing with Jaeger
- **Concepts Covered**:
  - Introduction to Jaeger and its architecture for distributed tracing.
  - Setting up Jaeger in a Kubernetes cluster using Helm.
  - Instrumenting services using OpenTelemetry to enable tracing.
  - Viewing and analyzing traces in the Jaeger UI.
  - Cleaning up the environment after setting up Jaeger.
- **Key Learning**:
  - Gain insights into distributed tracing and how it helps in debugging and performance optimization.
  - Learn how to set up and configure Jaeger for tracing in a microservices architecture.

### Day 7: OpenTelemetry – Setting Up Unified Observability
- **Concepts Covered**:
  - Introduction to OpenTelemetry, a unified framework for observability.
  - Understanding how OpenTelemetry integrates tracing, metrics, and logging.
  - Comparison of OpenTelemetry with prior observability tools like Jaeger, Prometheus
  - Supported programming languages and multi-language support in OpenTelemetry.
  - Step-by-step setup of OpenTelemetry in Kubernetes.
- **Key Learning**:
  - Learn how OpenTelemetry simplifies the process of collecting and exporting telemetry data.
  - Understand the benefits of a unified observability approach using OpenTelemetry.
  - Gain hands-on experience with setting up OpenTelemetry Collector, Prometheus, Jaeger, and Elasticsearch to monitor a Golang microservice application.
 



                        NODE AND CLUSTER IN ELASTICSEARCH

Node

A node is a single server that is part of your Elasticsearch cluster. It stores data and participates in the cluster's indexing and search capabilities. Each node has a unique identifier (node name) and can be configured with specific roles. Here are the primary types of nodes:

Master Node

Responsible for cluster-wide settings and state, managing the cluster, and coordinating operations like creating or deleting indices. Master nodes ensure the cluster is healthy.

Data Node: Stores data and handles data-related operations such as CRUD (create, read, update, delete) operations, search, and aggregations. These nodes are crucial for the actual data handling and querying.

Ingest Node: Preprocesses documents before indexing them. It runs ingest pipelines to transform and enrich the documents.

Coordinator Node: Routes requests to the appropriate nodes, managing the communication between client and data nodes. It helps offload some of the query processing burden from other nodes.

Machine Learning Node
Role: Dedicated to performing machine learning tasks within the Elasticsearch cluster.
Responsibilities: Runs anomaly detection jobs, performs data analysis, and processes machine learning tasks.
Best Practices: Deploy if you are using Elasticsearch's machine learning features. Ensure adequate resources for efficient processing.

      Cluster

A cluster is a collection of one or more nodes that together store all your data and provide federated indexing and search capabilities across all nodes. Here are some key features:

Cluster Name:
All nodes that belong to the same cluster must have the same cluster name. This name is used to identify the cluster when nodes join it.

Shards and Replicas:
Data in Elasticsearch is divided into indices, which are further divided into shards. Each shard can have replicas for redundancy and high availability. Primary shards store the original data, while replica shards store copies. 

High Availability: 
By distributing shards across multiple nodes, Elasticsearch ensures high availability. If a node fails, its shards can be recovered from the replicas on other nodes.( AZ deployment)

Cluster State: 
Managed by master nodes, the cluster state includes metadata about indices, shards, nodes, and other settings. It's crucial for cluster operations and health.

Sharding:
Elasticsearch divides indices into shards, which are distributed across multiple nodes. This allows for parallel processing and helps in scaling both storage and search capabilities.

                 DOCUMENTS 

JSON Format, INDEXING, NODE. SHARDING AND REPLICA SCHEMA-LESS IN ELASTICSEARCH
Key Concepts in Elasticsearch
JSON Format:
Description: Documents in Elasticsearch are represented as JSON objects. This format is easy to read and supports nested structures.
Benefit: Allows for flexible and hierarchical data representation.

Indexing:
Description: The process of storing data in Elasticsearch, making it searchable. Each document is indexed in an index (similar to a table in SQL).
Benefit: Enables efficient search and retrieval of data.

Nodes:
Description: Instances of Elasticsearch running on servers. Nodes can have different roles (master, data, ingest, etc.) to optimize the cluster’s performance.
Benefit: Scalability and load distribution across multiple servers.

Sharding:
Description: Dividing an index into smaller pieces called shards. Each shard is a fully functional index and can be distributed across multiple nodes.
Benefit: Improves search performance and allows for horizontal scaling.

Replica Shards:
Description: Copies of primary shards. They provide fault tolerance and high availability.
Benefit: Ensures data redundancy and load balancing for read operations.

Schema-Less:
Description: Elasticsearch does not require a predefined schema. Fields and mappings can be dynamically added.
Benefit: Flexibility in data structure, allowing easy updates and changes without downtime.

          INVERTED INDEX IN ELASTICSEARCH
          
An inverted index is the core data structure used by Elasticsearch for full-text search. It is optimized to speed up the process of finding documents that contain a given set of words.

How Inverted Index Works
Tokenization: When a document is indexed, its text fields are broken down into individual words or terms. This process is called tokenization.

Indexing Terms: Each term is then stored in a data structure where the term points to the documents (or fields) that contain it. This is the inverted index.

WHAT IS INDEX IN ELASTICSEARCH

 An index is a collection of documents that share similar characteristics. It can be thought of as a database table in relational databases.

Structure: Each index is composed of one or more documents, which are JSON objects. These documents contain fields (key-value pairs).

Elasticsearch Index Concepts:

Index: A collection of documents with similar characteristics.

Shards and Replicas: Ensure scalability and high availability.

Mappings: Define the structure and data types of documents.

Index Management: Involves creating, updating, searching, and deleting indices.


                SHARDS AND REPLICAS IN ELASTICSEARCH


Shards and replicas are fundamental concepts in Elasticsearch that ensure scalability, performance, and fault tolerance.

Shards
Definition:  A shard is a basic unit of storage in Elasticsearch. Each index can be divided into multiple shards.

Think of shards as smaller subsets of an index that can be managed independently.

Types:

Primary Shards: Store the actual data.

Replica Shards: Copies of the primary shards for redundancy and fault tolerance.

Benefits:

Scalability: By dividing an index into multiple shards, Elasticsearch can distribute the data and search load across multiple nodes.

Parallelism: Allows for parallel processing of data, improving query performance.

Replicas

Definition: Replicas are copies of primary shards. Each primary shard can have multiple replicas.

Replicas ensure data is not lost in case of node failures and improve search performance by allowing read requests to be served by both primary and replica shards.

Benefits:

High Availability: Provides fault tolerance by replicating data across multiple nodes.

Load Balancing: Improves search performance by distributing read requests between primary and replica shards.

How They Work Together
Data Distribution: When an index is created, its data is distributed across the defined primary shards. These shards are then distributed across the nodes in the cluster.

Replication: Each primary shard’s data is copied to its replica shards, which are also distributed across the nodes.

Failover: If a node holding a primary shard fails, a replica shard can be promoted to a primary shard to ensure no data loss.


                MAPPING ELASTICSEARCH

Mapping in Elasticsearch defines how documents and their fields are stored and indexed. It specifies the data types for each field, the analyzers to be used, and various indexing options

Mappings: Define the structure and data types of documents.

Field Types: Specify how each field is indexed and stored.

Dynamic Mapping: Automatically detect and add fields.

Explicit Mapping: Manually define mappings.

Analyzers: Process text fields during indexing and querying.

            DYNAMIC MAPPING IN ELASTICSEARCH

Dynamic mapping in Elasticsearch is a powerful feature that allows the system to automatically detect and create mappings for new fields as they are added to the index. This means you don't need to define the structure of your documents beforehand2. When you index a document, Elasticsearch will automatically create the necessary fields and data types based on the content of the document.

Here are some key points about dynamic mapping:

Automatic Field Creation: When a new field is detected in a document, Elasticsearch dynamically adds it to the type mapping.

Dynamic Parameter: You can control this behavior using the dynamic parameter, which can be set to true, false, or runtime.

Customization: You can customize dynamic mapping rules using dynamic templates to define custom mappings for dynamically added fields.

Date Detection: By default, Elasticsearch tries to detect date fields and formats them accordingly. This can be customized or disabled3.

Disabling Dynamic Mapping: If you don't want Elasticsearch to automatically create fields, you can set the dynamic parameter to false.


             CRUD OPERATION ON ELASTICSEARCH

CRUD operations are fundamental to working with databases, including Elasticsearch. CRUD stands for Create, Read, Update, and Delete

             Summary

Create: Use PUT or POST to add new documents to an index.

Read: Use GET to retrieve documents.

Update: Use POST with the _update endpoint to modify documents.

Delete: Use DELETE to remove documents from an index.

                   Real-World Example: Kubernetes Log Management

In a Kubernetes environment, Fluent Bit can be deployed as a DaemonSet, ensuring that it runs on every node in the cluster. It collects logs from the /var/log/containers directory and forwards them to Elasticsearch. Kibana can then be used to visualize these logs, making it easier to monitor the health and performance of your applications and the Kubernetes cluster itself

                 INTRODUCTION TO KIBANA
                 
Kibana is a powerful and user-friendly data visualization and exploration tool for Elasticsearch. It's part of the Elastic Stack, also known as the ELK Stack (Elasticsearch, Logstash, Kibana).

  IMPORTANT OF DATA VISUALISATION

1 Simplification of Complex Data

Understanding Made Easy: Transforms complex data sets into visual representations, making them easier to understand.

Pattern Recognition: Helps identify trends, correlations, and outliers quickly.

2 Enhanced Communication

Effective Storytelling: Visualizations help tell a story, providing context and insights that support better decision-making.

Clear Communication: Makes it easier to communicate findings to stakeholders, regardless of their technical expertise.

3 Increased Engagement

Interactive Dashboards: Engage users and allow them to explore data more deeply.

Visual Appeal: Captures attention and makes presentations more engaging.

4 Accelerated Decision-Making

Quick Insights: Enables faster identification of key insights, leading to more timely and informed decisions.

Data-Driven Culture: Promotes a culture of data-driven decision-making within organizations.

5 Identification of Patterns and Relationships

Trends Analysis: Helps in analyzing trends over time and across different dimensions.

Correlation Identification: Makes it easier to spot relationships between different variables.

          BASIC CHART, TIME SERIES VISUALISATION, GEOSPATIAL VISUALISATION
          
Basic Charts: Visualize data comparisons, distributions, and parts of a whole using bar charts, line charts, pie charts, and histograms.

Time Series Visualization: Track and analyze data over time to identify trends, make forecasts, and monitor real-time events using line graphs and area charts.

Geospatial Visualization: Understand geographic patterns and relationships using choropleth maps, heat maps, and point maps.
          
       KIBANA QUERY LANGUAGE KQL

The Kibana Query Language (KQL) is a simple, text-based query language used in Kibana to filter data. It's designed to be easy to use and understand, making it accessible even for those who are new to querying data

Comparison with Lucene Query Language
KQL is different from the Lucene Query Language, which is more powerful and flexible but also more complex. KQL is designed for simplicity and ease of use, while Lucene provides more advanced querying capabilities2.

Example Use Cases

Log Analysis: Filter logs to find specific events or errors.

Security Monitoring: Identify suspicious activities by filtering relevant fields.

Performance Monitoring: Track performance metrics and filter based on thresholds

            BUILDING DASHBOARD MAPS WITH KIBANA

Use Cases with Brief Examples

1 Log Analysis: Visualize the Geographical Distribution of Log Events

Example: Suppose you have log data from multiple web servers around the world, each log entry includes the IP address of the request origin. You can use Kibana maps to plot these IP addresses, showing where log events are coming from globally.

2 Security Monitoring: Track the Locations of Security Incidents

Example: If you collect data on failed login attempts with geographical coordinates, you can use Kibana to create a map that displays the locations of these security incidents, helping you identify regions with higher risks.

3 Performance Monitoring: Monitor the Performance of Services Across Different Regions

Example: You have performance metrics data, including response times and their corresponding locations. Using Kibana maps, you can visualize areas with slow response times, allowing you to focus on regions that need performance improvements.

             INTRODUCTION TO FLUENTBIT


