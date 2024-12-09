
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

Data Node: 

Stores data and handles data-related operations such as CRUD (create, read, update, delete) operations, search, and aggregations. These nodes are crucial for the actual data handling and querying.

Ingest Node:

Preprocesses documents before indexing them. It runs ingest pipelines to transform and enrich the documents.

Coordinator Node:

Routes requests to the appropriate nodes, managing the communication between client and data nodes. It helps offload some of the query processing burden from other nodes.

      Cluster

A cluster is a collection of one or more nodes that together store all your data and provide federated indexing and search capabilities across all nodes. Here are some key features:

Cluster Name:
All nodes that belong to the same cluster must have the same cluster name. This name is used to identify the cluster when nodes join it.

Shards and Replicas:
Data in Elasticsearch is divided into indices, which are further divided into shards. Each shard can have replicas for redundancy and high availability. Primary shards store the original data, while replica shards store copies.

High Availability: 
By distributing shards across multiple nodes, Elasticsearch ensures high availability. If a node fails, its shards can be recovered from the replicas on other nodes.

Cluster State: 
Managed by master nodes, the cluster state includes metadata about indices, shards, nodes, and other settings. It's crucial for cluster operations and health.



