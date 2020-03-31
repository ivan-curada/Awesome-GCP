# Introduction to GCP Products/Services

## The Google Cloud Developer's Cheat Sheet

<https://github.com/gregsramblings/google-cloud-4-words>

- links out to a Marketing page and a Developer Documentation

## Products/Services as Building Blocks

Each Product/Service has its own functionality like shapes in Lego blocks.

Important Products

- Compute Products
- Storage Products
- Networking Products

### Cloud Deployment Manager

- Templated Infrastructure Deployment
- under Management Tools Products

### GCP Marketplace

- under API Platform and Ecosystems
- Partner & Open-source Marketplace
- aka Cloud Launcher

## Key Building Blocks

### Compute Products

1. Compute Engine
    - Virtual Machines, Disk, Network
    - rent by a second
2. Cloud Function
    - Event-driven serverless functions
    - rent by a tenth of a second
    - FAAS, manages all of the scaling
3. Kubernetes Engine
    - Managed Kubernetes/Containers

### Storage Products

1. Cloud Storage
    - object storage and serving
    - serverless
    - Nearline
        - Archival Occasional Access Storage
    - Coldline
        - Archival Rare Access Storage
2. Persistent Disk
    - VM-attached Disks
    - block storage
3. Cloud Filestore
    - Managed NFS Server
    - file storage

### AI and Machine Learning Products

1. Cloud TPU (Tensorflow Processing Unit)
    - Specialized Hardware for ML
    - compute engine instance

### Database Products

1. Cloud SQL
    - managed MySQL and PostgreSQL
    - managed read replicas
2. Cloud Spanner
    - Horizontally Scalable Relational DB
3. Cloud Firestore
    - Strongly-consistent serverless Document DB
4. Cloud Datastore
    - Horizonatally Scalable Document DB
5. Cloud BigTable
    - Petabye-scale, low-latency non-relational DB

### Data and Analytics Products

1. Cloud Dataflow
    - Stream/batch data processing
    - Apache Beam
2. Cloud Dataproc
    - Managed Spark and Hadoop
    - uses Compute Engine under the hood
3. Cloud Pub/Sub
    - Global Real-time Messaging
    - connect anything to anything else
    - publish/subscribe topics
4. Cloud BigQuery
    - Data Warehouse/Analytics
    - serverless

### Networking Products

1. Virtual Private Cloud
    - Software Defined Networking
2. Dedicated Interconnect
    - Dedicated private network connection
    - VPC to external data center
3. Cloud NAT
    - Network Address Translation Service
4. Cloud Load Balancing
    - Multi-region Load Distribution
5. Network Service Tiers
    - Price vs Performance Tiering
    - allows clients connecct to 1 IP address and still connect to server in VPC physically closer to them
    - handles re-routing also
6. Cloud Armor
    - DDoS protection and WAF
7. Cloud CDN
    - Content Delivery Network
8. Cloud DNS
    - Programmable DNS Serving
    - 100% uptime guarantee

### Management Tools Products

1. Stackdriver Monitoring
    - Infrastructure and Application Monitoring
    - watch metrics
2. Stackdriver Logging
    - Centralized Logging
3. Stackdriver Debuuger
    - Live Production Debugging
4. Stackdriver Error Reporting
    - App Error Reporting
5. Strackdriver Profiler
    - CPU and heap profiling
6. Stackdriver Transparent SLIs
    - Monitor GCP Services
7. Stackdriver Trace
    - App Performance Insights

### Identity and ecurity Products

1. Cloud Identity
    - Manage Users, Devices, and Apps
    - if not using GSuite
2. Cloud IAM
    - Resouce Access Control
    - ties everything together in a security perspective
    - defines who can do what to which things
3. Cloud HSM
    - Hardware Security Module Service
    - manage encryption keys and certificates
4. Cloud Data Loss Prevention API
    - Classify, Redact Sensitive Data
    - ML service
