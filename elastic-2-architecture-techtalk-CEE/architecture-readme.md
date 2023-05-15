# Tech Talks for Eastern Europe

We're pleased to announce the launch of our series of tech talks for Eastern Europe, where we'll be exploring technical topics and features that our audience is most interested in.

As a Solution Architect at Elastic for the past three years, I've learned that Eastern Europe teams are looking for technical how-to's and feature-wise explanations. That's why we've created this series of tech deep dive presentations and demos to provide you with the information you need.

## Data Visualizations with Kibana Dashboards

The webinar covers various topics related to designing, implementing, and managing Elasticsearch clusters for optimal performance, scalability, and resilience. It starts with an overview of Elasticsearch and its core features, such as full-text search, analytics, and real-time data processing. It then delves into the key components of an Elasticsearch cluster, including nodes, shards, indices, and clusters.

The webinar discusses the different types of nodes and their roles, such as data nodes, master nodes, and client nodes. It also covers the best practices for allocating shards and replicas across nodes to balance workload and ensure fault tolerance.

The webinar provides insights into various aspects of Elasticsearch cluster architecture, such as network topology, security, monitoring, and backup and recovery. It emphasizes the importance of designing a resilient and secure cluster architecture that can handle high volumes of data and queries while maintaining data integrity and availability.

Throughout the webinar, the presenter provides examples of common Elasticsearch use cases and shares best practices and tips for optimizing cluster performance, such as using efficient search queries, tuning indexing settings, and leveraging caching and routing features.

In summary, the webinar offers a comprehensive and practical guide to Elasticsearch cluster architecture and best principles, equipping attendees with the knowledge and tools they need to design and manage Elasticsearch clusters that meet their specific business needs.

## Course 0  Intro to Architecture design principles / best practices 

## Course 1  Cluster, nodes, sharding, sizing and more

## Course 2  Cross Cluster Search / Cross Cluster Replication

## Course 3  Data management ILM, SLM

## Course 4  Searchable Snapshots

## Course 5  Deployment

## Course 6 Agent, Kibana & co


02_À LA CARTE_Architecture Webinar 1406

https://events.elastic.co/elasticalacarte

Running an Elasticsearch cluster is actually quite simple, but sometimes it's hard to decide how many nodes to deploy and where. In this session, we'll cover what an Elasticsearch node is, how we deal with the requirements for a flexible and efficient architecture, and how to plan the cluster with a big volume of data to be ingested and stored. We'll also share some best practices to be aware of when planning an Elasticsearch cluster: what is ILM, how hot nodes differ from cold nodes, what are the minimum requirements per zone, what are searchable snapshots, when they can be useful. And what are SLM, CCS and CCR and when to apply them.  


You'll also have the opportunity to ask Elastic experts questions about your cluster architecture.

WHY - WHAT - HOW
The goal is to ensure that you are aware of all the small things we take into consideration and in case you hear “it depends” it mostly depends on you and how clear are the requirements and expectations to your projects. As with most things in IT, not all of these are black and white requirements, and it is important to consider the context and requirements of your business in conjunction with these best practices.

Course 0  Intro to Architecture design principles / best practices 
Architecturing Basic concepts: 
use case (search, observability, security, hybrid), mission/business-critical
project requirements or constraints (data sources, automatisations, alerts, analytics, queries), 
data ingest workload (GB a day/ number of endpoint security, queries per second and response time), 
users (5-100-10000)

Elastic Architecturing for HA, scalability, recoverability and security
High Availability: (SLA) Continuous and uninterrupted functionality without a single point of failure in operations and with redundancy in critical components, use-case specifics (search - end-users, observability - SREs, security - security team)

A highly available system is designed to provide continuous and uninterrupted
functionality. This is done by removing single points of failure in operations and introducing redundancy to critical components (such as storage and data processing). Failures in software or hardware cannot be fully eliminated when running IT operations
at scale. High availability is important for a system to be available when needed by users,
despite the (often unpredictable) failures or errors in the underlying infrastructure.

Scalability use case specifics (Black Friday: search, business operability, attacks), write/read operations, adding/scaling down number of nodes, shard allocation strategy, tests
Generally, scalability can be achieved by monitoring resource consumption on a system and automatically increasing or decreasing the allocation of resources. A scalable system adds resources when there is demand, but it also should remove resources to optimize for cost when demand dissipates.

Teams can measure system scalability by running regular performance benchmarks and tests with expected data workloads against the Elasticsearch cluster. Where automatic scaling is not possible or desired, capacity planning exercises can be leveraged to forecast and plan the growth of your data, as well as the corresponding resources that are required to run each layer of the stack.

Recoverability (RTO/RPO), active/active architecture with logstash, active/passive architecture with CCR, Snapshots with SLM 
• Recovery Time Objective (RTO), which defines the maximum allowed duration of
time it takes to restore the system from a state of disaster
• Recovery Point Objective (RPO), which defines the tolerance for the volume of
data or state that can be lost during a disaster

Security: secure access to your data, protect data in transit, protect data at rest, enforce network segmentation, make solution auditable and traceable, 

Maintenance and administration: prod/dev, upgrade, restarts, patches

Specialized architectures: 
federated searching aka CCS for geographical proximity (latency)
cross-cluster replication CCR  for DR and geographical proximity (highly available and fault-tolerant )
tiered architectures to handle complex requirements (ILM, hot-warm-cold-frozen (high level, later in details); searchable snapshots (high level, later in details))

Elastic deployment bare metal, cloud, ECE/ECK, monitoring the cluster, benchmark and plan capacity

Course 1  Cluster, nodes, sharding
Basic concepts: what is a node, index, shard, shard sizing, number of replicas
Why → scalability resilience ingest performance 
What use case, ingest, analytics\queries, 
Dedicated nodes, three masters, 
Type of shards, number of shards, disk utilization 
Data ingestion or write operations can be scaled by increasing the number of primary
shards on an index to improve concurrency and resource availability across Elasticsearch
nodes. The number of primary shards for an index is immutable once an index is created;
this means that while it is relatively easy to scale for write throughput, it is not trivial to
dynamically scale resources up and down on Elasticsearch based on changing traffic patterns.

Elasticsearch will not allocate shards to nodes with disks that are 85% utilized.
Elasticsearch will attempt to move shards from nodes with disks that are 90% utilized.


Documentation for small /large deployments

Course 2  Cross Cluster Search / Cross Cluster Replication
One cluster or number of clusters, DR, CCR, 
CCS, active-active architecture, active-passive architecture, 
DMZ, network segmentation

Course 3  Data management ILM, SLM
Difference between hot-warm-cold-frozen
ILM policy, approaches (size, date, ), functions and skipping phases, data streams (page 128)
SLM policy and repository size, impact on performance

Course 4  Searchable Snapshots
Difference ssnaps and regular snaps
Repositories S3, file system etc.
Cold size and fully mounted indexes
Frozen zone and partially mounted indexes
HW resources and for cold and frozen
Benchmarking the performance 

The following considerations apply to Snapshots on Elasticsearch:
Snapshots can be taken on a running cluster; an appropriately resourced cluster should not experience performance degradation for search and ingest when a snapshot is taken.

A snapshot creates a copy of the underlying Lucene segments containing your data. Snapshots do not contain raw data and can only be restored on an appropriately versioned Elasticsearch cluster.
A snapshot repository is used to define the destination of your Snapshots.
A Snapshot Life Cycle Management (SLM) policy can be used to define various configuration and retention behaviors, including the period when Snapshots are taken, what data is coped, and how long Snapshots are retained before they are deleted.
Snapshots are incremental when they're run. As Lucene segments are immutable, a snapshot will simply keep track of all the segments in a cluster and copy any new segments as needed. As a result, the amount of storage that's consumed on your storage services will be roughly the equivalent of the size of your primary shards.

Course 5  Deployment
Cloud: templates, autoscaling, update, scale up/scale down, monitoring, SLM
On-prem: ansible playbooks, scripts, updates, planing proper HW; maintenance of several clusters
ECE: why people move, success story

Course 6 Agent, Kibana & co
Core components of the stack: Kibana (solutions and use cases), Elasticsearch (data storage and analytics), Logstash/Beats/Agent (Data collection and ingestion) 
Page 410 The visualization and solution layer can be made highly available by running at least two instances of Kibana across availability zones, configured to work with the underlying Elasticsearch cluster. Kibana is a stateless component and uses Elasticsearch to persist settings, configuration, and use case data. As such, it is relatively easy to improve availability by load balancing across a pool of Kibana instances.

