# Storage and Database Services

## NoSQL

- semi-structured
- flexible schema
- no joins

## BigTable

- Wide Column Database
- Petabyte scale
- low latency and high availability
  - low latency writes in high volume
  - IoT streams
- designed for analytics
  - large volume
- expensive service
- managed but not serverless
  - needs to create an instance
- Instance Types
  - Development
    - low cost
    - does not provide high performance and high availability
  - Production
- Storage Types
  - HDD
    - only if no need for high IOPS
  - SDD
- Clusters
  - can specify more than one cluster in one instance
  - Location (Region and Zone)
  - Nodes
    - stores metadata about its data
    - includes where data is stored in Collosus (Google's Storage System)
    - recommended : 3 as minimum
  - Replicated Cluster
    - replica in different region
- Monitoring
  - CPU Utilization
    - if high, add more nodes
  

## Datastore

- Document database
- JSON structre
- heirarchical
- Modes
  - determines which storage system is used
  - Native Mode
    - Enables Firestore feature
      - real time synchronization
  - Datastore Mode - recommended
    - Cloud Datastore behavior API
    - runs on top of Firestore storage layer
- no need to specify machine type
- serverless
- choose region location
- one database per project

### creating entities and indexes

- entities - similar to SQL record
  - exists in a namespace in a datastore
    - group entities by namespace
  - kind = analogous to table
  - key identifier
  - properties
    - name + datatype + value
    - can differ from each entities
  - enable "index this property"
    - allows entities to be queried using that property
- Indexes == Composite Indexes
  - indexing using two properties 

## Firestore

- Document Database - Datastore Native Mode
- real time synchronization
  - great for mobile apps

## Relational Database

- structured data
- requires SQL
- ACID transactions
- complex queires
-joins

## SQL

- Regional Relational storage
- managed MySQL and PostgreSQL service
- upto 10TB
- setup
  - name
  - root password
  - location
  - db version
  - set connectivity (public or private IP)
  - machine type and storage type
    - use SSD
  - default enabled: backups automated
  - default enabled: failover replica
    - high availabiltiy
  - database flags
  - maintenance schedule: default enabled

## Spanner

- Horizontally-scalable Global database
- strong consistency of data across multiple regions
- instance = set of VMs running the Spanner db
- id = name
- location
  - regional
  - multi-regional
    - eur2 (belgium/netherlands)
    - nam4 (north virginia/ south carolina)
    - nam6 (iowa/south carolina/oregon/los angeles)
  - global
    - nam-eur-asia1 [north america(iowa), europe(belgium), asia(taiwan])
  - allocate nodes: 3 (minimum)
  - recommended to use CLI in setting up db
- metrics
  - CPU utilization - average across all nodes

## FileStore

- managed Network File System

## Persistent Disk

- Block Storage
- used with VMs
- persist data even when VM shuts down

## Cloud Storage

- Object Storage
- large unstructured data
- archived adata
- temporary storage between service
- Global Access
- Web accessible
- Buckets, folders, projects
  - names 
    - should be globally unique
  - region
    - multi-region - high availability
    - regional
    - dual-region
  - Encryption
- Storage Classes
  - Standard
  - Nearline
    - less than a month access
  - Coldline
    - less than a year access
- Access Control 
  - Uniform
    - same access level in all objects in the bucket
  - Object and Bucket Level
    - individual access control
- Life Cycle Rules
  - change storage class
    - object condition
  - coldline objects cant be changed to nearline
- gsutil command line tool