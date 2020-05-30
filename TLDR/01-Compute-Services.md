# Compute Services

## Compute Engine

### Create Virtual Machines

- instance ID
- machine type
  - default: n1-standard-1 (1VCPU, 3.75GB)
  - shared core
    - single hardware hyperthread
    - non-intensive and supports CPU bursting
    - g1-small (1vCPU, 1.7MB)
    - f1-micro (1vCPU, 614MB)
- network interface
- machine type series
  - N1 (1st gen)
    - skylake CPU platform
  - M1 (memory optimized)
    - Intel Skylake CPU
    - Mega-memory
    - Ultra-memory
  - C2 (compute optimzed)
    - Intel Cascade Lake CPU
  - N2 (2ns gen)
    - Intel Cascade Lake
  - E2 (2nd gen)
    - CPU platform based on availability
  - N2D (2nd gen)
    - AMD EPYC Rome
- Persistent Disk / Boot disk
  - default: standard
  - size - default 10GB
  - IOPS
    - use SSD for better IOPS performance
  - choose OS image
    - windows, linux etc
    - default: Debian GNU/Linux 10

``` cli
gcloud compute instance create [NAME] \
--zone [ZONE] \
--machine-type [machine type] \
--bootd-isk-size [] \
--image [OS]
```

### Attaching Additional Disk

- Create isntance > Management, Security, Disk, Networking & Sole tenancy > Disk > Add Disk
- Compute Engine > Disk > Physica; Block Storage

### Attaching GPUs

- Create Instance > CPU  platform & GPU

``` cli
gcloud compute instances create [NAME] \
--accelerator-type [GPU model] \
--accelerator-count [number of GPUs]
```

### Custom Machine Types

- sliders
  - vCPUs
  - Memory

``` cli
gcloud compute instances create \
--custom-cpu [#]
--custom-memeory [#(GB default)], type "MB when needed
--custom-vm-type [N2]
or
--machine-type [n2-custom-#cpu-#MB]
```

### Creating Snapshots

- Snapshots are useful for backing up data, copying a persistent disk, and even, creating a custom image. Snapshots can be created from persistent disks even while they are attached to running instances.
- compute engine > snapshots > create

``` cli
gcloud compute disks snapshot [disk_name] \
--storage-location [storage bucket] \
-- region [region]
```

### Creating Images

- A machine image is a Compute Engine resource that stores all the configuration, metadata, permissions, and data from one or more disks required to create a Virtual machine (VM) instance. 


```cli
gcloud compute images create image-name \
  --source-disk source-disk \
  --source-disk-zone zone \
  --family image-family \
  --storage-location location \
  --force

gcloud compute images create image-name \
  --source-image source-image \
  --source-image-project image-project \
  --family image-family \
  --storage-location location

gcloud compute images create image-name \
  --source-snapshot source-snapshot \
  --storage-location location
```

### Preemptive VMs

- 80% discount
- 24-hour use before shutdown
- will no live migrate and auto restart

- Create VM > Management, Disk, Security, Sole Tenancy > Availability Policity > Pre-emptibility > ON

### Shielded VMs

- Virtual machines (VMs) on Google Cloud hardened by a set of security controls that help defend against rootkits and bootkits.

### Sole Tenancy

- instances in the same physical server
- Sole-tenant nodes are physical Compute Engine servers dedicated solely to your workloads. Sole-tenant nodes offer the same machine types and options as regular compute instances, including custom machine shapes and transparent maintenance, but on servers dedicated exclusively to your use

### Instance Groups

- collection of Instances managed a single identity

### Managed Instance Groups

- multiple identical VMs
- configuration defined in instance template
- feature
  - auto scaling
  - auto healing
  - multizone - high availability
  - auto update

#### Autoscaling in Instance Group

- Health Check
  - protocol + port checks
- Cooldown period
  - time to wait before reading autoscaling metric
  - time allowed for isntance to first initialize
  - autoscale does not collect metrics
- Stabilization period
  - time autoscale uses to calculate MIGS recommended target size
- avoids thrashing (rapidly adding and removing instances)

### Umanaged Instance Groups

- multiple possibly heterogenous VMs
- used to applu load balancing across heterogenous groups
- recommended for legacy clusters only
- no autos scaling, auto healing or auto updating

## Kubernetes Engine

- Orchestration Platform
- manage clusters and organize containers
- runs containers on cluster of virtual or physical machines
- features
  - load balancing of workloads
  - node pools to segment nodes with cluster
  - auto ehaling
  - operations monitoring
- app == workloads
- single cluster master, multiple worker nodes


### Kubernetes Architecture

- Pod
  - encapsulating and running containers
  - run multiple pods of the same container
    - specified in a deployment
- Deployment
  - specification of parameters
    - set of pods executing a particular conainter
  -need to know IP address of pod fpr API
- Services
  - Three types of services:
    - ClusterIP - exposes the service or group of pod/deployments on an internal IP
    - NodePort - exposes the service/pod/deployment to the node
    - LoadBalancer - exposes the service/pod/deployment externally with external IP
  - mechanism for service discovery
  - IP address for load balance service
  - determines what pods available
  - wraps the deployment
- Node-Pool
  - implemented as MIGs
  - a node runs in an instance

### Storage Objects

- Peresistent Volume
  - unit of storage outside the pod
  - exists even of pod shutdowns
- Persistent volume claims
  - allows pod to access the volume

### Creating a Cluster

``` cli
gcloud container clusters create [name] \
--zone [zone] \
--disk-size [] \
--machine-type []
```

### Managing Clusters

- `kubectl`
  - runs command to k8 cluster
  - complements `gcloud container` to manage clusters
- operations 
  - autoscale
  - cluster-info
  - config
  - create
  - delete
  - descrbe
  - expose (a service)
  - run (an image)

| `gcloud container` | `kubectl` |
| --- | --- |
| on the cluster | in the cluster |
| setting up k8 clusters, adding nodes | manipulating abstraction/data in k8 clusters |

### Monitoring k8 Clusters

- enable Logging and Monitoring metrics
- Infrastructure
  - cluster > node > pods
- Workloads
  - clusters > kube system > workloads
  - clusters > app > workloads
- Servuces
  - clusters > kube system > high level services

### Viewing Status of k8 clusters

- k8 enging console
- node-pool
  - status
  - machine type
  - CPU - memory - storage

## App Engine

- Serverless
- PAAS
- microservices
- can run containers

### App Engine Standard

- runs app in preconfigured containers
- secure sandbox
- autoscales
- Components
  - app
  - service
  - version
  - instance
- Runtimes
  - Python
  - Java
  - NodeJS
  - PHP
  - Ruby
  - Go

### App Engine Flexible

- runs customized Docker container
- Runtime
  - java
  - Python
  - Ruby
  - PHP
  - custom
- can be ran locally with App Engine SDK
- custom health checks
- higher CPU and memory limits
- regional anaged instance group
  - not zonal MIGs
  - higher availability

### Deploy

- app.yaml
  - app engine runtime
  - script to run

```cli
gcluod app deploy app.yaml
gcloud app browse
```

### Scaling

- executes an App Engine managed isntance
- scale based on load when running dynamic instances
- can configure resident isntances to run at all times but whe nautoscaling is enabled, use dynamic instances
- Types of Scaling:
  - Manual
    - use resident instances continuously irrespective of load level
  - Basic 
    - scales by number of requests
  - Automatic 
    - scales based on request rate, response latencies, and application metrics
- app.yaml configuration
  - target-cpu-ultiization
  - target-throughput-utilization
  - max-concurrent-requests
  - max-pending-latency
  - min-pending-latency

### Traffic Splitting

- possible for multiple app versions
- methods
  - IP address
    - can create problems if app is staeful and user changes IP
  - HTTP cookie
    - preferred
    - http request header for cookie contains hash value
      -`GOOGAPPUID`
  - random selection
    - useful for stateless apps
    - no need to ensure traffic from a client always go to the same instance
    - no `GOOGAPPUID`

### Ensuring App Engine Components are installed and updated

```cli
gcloud components install app-engine-language
```

## Cloud Functions

- Event-driven functions
- serverless
- configuration
  - name
  - memory - default 256MB
  - event trigger
  - source code
- GCP resources
  - Cloud Storage
  - Pub/Sub
  - HTTP
  - Firebase
  - Operations Logging
- Events
  - Storage
    - upload
    - delete
    - archive
  - Pub/Sub
    - publish message
  - HTTP
    - post, get, put, delte, update
- Triggers
  - declaration of interest in event
  - bind function to a trigger to execute
- Function
  - executable code
  - NodeJS, Python, Go

### CLI

``` cli
gcloud functions deploy [app-name] \
--runtime [language] \
--trigger-resource [resource_id] \
--trigger-event [google.service.resource.command] \
--source [source code, zip file in cloud storage]
```

- 
