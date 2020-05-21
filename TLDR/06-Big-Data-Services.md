# Big Data Services

## Pub/Sub

- Message Queue
  - one application writes message
  - another application reads message
  - asynchronous
- Topic
  - structure for storing messages
- Subscription
  - enables applications read messages in queue
- Delivery Type
  - Pull
    - program processing the messages to control whe nthe message is read
    - the program reading the message control when it is read wiht a pull subscription
  - Push
- Subscription Expiration
  - will expire if there is no activity
  - def: 31 days
  - max 365 days
- Acknowledgement deadline
  - time that a program has to tell pub/sub that it has read and acted oon the message and its okay to delete the message
  - if there is no acknowledgement, the message will be sent again
  - def: 10 seconds
  - max 600 seconds
- Message Retention Duration
  - def: 7 days (max)
  - min: 10 mins
- Retain acknowledged messages
  - when enabled, acknowledged messages are retained for the message retention duration.
- Snapshot
  - save state of the topic

## Dataproc

- Managed Hadoop and Spark
  - big data analytics platform
- manages Hadoop clusters
- ETL jobs
- large batch processing
- lift and shift migration from on prem to cloud

### Create Clusters

- name
- location (region, zone)
- Cluster Mode
  - Single Node (1 master, 0 workers)
    - development and testing
  - Standard (1 master, N workers)
    - when master node goes down, access to cluster is gone
  - High Availability (3 masters, N workers)
- Master Node Machine Type
  - default: 4vCPUs, 15GB memory
- Primary Disk
  - 500GB default
- Worker Nodes
  - actual nodes that does the computation/analytics
  - vertical scale (increate vCPUs, few nodes)
  - horizontal scale (small vCPUs, more nodes)
  - minimum nodes = 2
  - local SSDs
- Advanced Options
  - network
  - cloud storage
  - Pre-emptible Worker Nodes
    - runs upto 24 hours
    - less expensive
    - when one of the nodes goes down, dataproc will start a new node
- Cloud Storage Bucket
  - staging bucket in moving data
- Batch Jobs
  - Job ID
  - location (region)
  - cluster
  - type
    - Hadoop - batch processing system
    - Spark - distributed in-memory big data processing system, java
    - SparkR - R
    - PySpark - Python
    - Hive - Haddop
    - SparkSql
    - Pig - Hadoop
    - Presto

## DataFlow

- Stream and Batch processing with Apache Beam
- runs jobs written in Java or Python
- build job from a template
- read data, do transformation, the write to storage
- managed service
- serverless
- "stream of time series data and create summary statistics for each minute of data"

## Cloud Storage Transfer

- transfering large volume of data between buckets
- transfer one cloud bucket to GCP storage bucket
  - can be from AWS s3
- can also be for scheduled job
  - specify some parameteres and an operator
- serverless

## BigQuery

- Data warehouse
- large scale data analysis
- petabyte scale
- SQL query language
- some support for joins
- not transactional
- bq command line tool
- Resource
  - Connection
    - Connect to Cloud SQL/Spanner

### Big Query Data Transfer Service

- load data from SAAS
  - AWS S3
  - Google Ad Manager
  - Google Play
  - Youtube
  - Cloud Storage


## Cloud Transfer Appliance

- transfer 30TB of data to cloud Storage from on premises data center
- offline data transfer
- 100TB ot 400TB of raw capacity per appliance