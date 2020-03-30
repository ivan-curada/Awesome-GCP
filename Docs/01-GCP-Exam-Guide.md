# Google Cloud Certified - Associate Cloud Engineer Exam Guide

<https://cloud.google.com/certification/cloud-engineer>

## Associate Cloud Engineer

- deploys applications, monitors operations, and manages enterprise solutions
- able to use Google Cloud Console and the command-line interface to perform common platform-based tasks to maintain one or more deployed solutions that leverage Google-managed or self-managed services on Google Cloud

## The Associate Cloud Exam Guide

<https://cloud.google.com/certification/guides/cloud-engineer>

### Set up a cloud solution environment

- Set up cloud projects and accounts
  - create projects
  - assign users to predefined IAM roles
  - manage uses in `Cloud Identity`
    - manual
    - automated
  - enable APIs within projects
  - provision one or more `Stackdriver` workspaces
- Manage billing configuration
  - create one or more billing account
  - link projects to a billing account
  - establishing billing budgets and alerts
  - setting up billing exports to estimate daily/monthly charges
- Install and configure the command line interface (CLI), specifically the `Cloud SDK`

### Plan and configure a cloud solution

- Plan and estimate GCP product use using `Pricing Calculator`
- Plan and configure `compute resources`
  - Select appropriate choices for given workload
  - using preemptible VMs and custom machine types as appropriate
- Plan and configure `data storage` options
  - Product choice
  - Choose storage options
- Plan and configure `network resources`
  - differentiate load balancing options
  - identify resource location in a network for availability
  - configure `Cloud DNS`

### Deploy and implement a cloud solution

- Deploy and implement `Compute Engine` resource
  - launch compute instance using `Cloud Console` and `Cloud SDK`
    - assign disks
    - availability policy
    - SSH keys
  - create an autoscaled managed instance group using an `instance template`
  - generate/upload a `custom SSH key` for instances
  - configure a VM for `Stackdriver` monitoring and logging
  - assess compute quotas and request increases
  - instal the `Stackdriver Agent` for monitoring and logging
- Deploy and implement `Google Kubernetes Engine` resources
  - deploy a `Google Kubernetes Engine cluster`
  - deploy a container application to GKE using `pods`
  - configuring `GKE application monitoring and logging`
- Deploy and implement `App Engine`, `Cloud Run`, and `Cloud Functions` resources
  - deploy an application
  - update scaling configuration, verstions
  - traffic splitting
  - deplou an application that receives `Google Cloud` events
    - `Pub/Sub` events
    - `Cloud Storage` object change notification events
- Deploy and implement `data solutions`
  - Initialize `data systems` with products
  - Load data
    - command line upload
    - API transfer
    - import/export
    - load from `Cloud Storage`
    - stream data to `Cloud Pub/Sub`
- Deploy and implement `network resources`
  - create a VPC with subnets
    - custom-made VPC
    - shared VPC
  - launch a `Compute Engine` instance with custom network configuration
    - internal-only IP address
    - Google private access
    - static external and private IP address
    - network tags
  - create ingress and egress firewall rules for VPC
    - IP subnets
    - tags
    - service accounts
  - create a VPN between Google VPC and external network using `Cloud VPN`
  - create a load balancer to `distribute application network traffic to an application`
    - `Global HTTP(S)` load balancer
    - `Global SSL Proxy` load balancer
    - `Global TCP Proxy` load balancer
    - `regional network` load balancer
    - `regional internal` load balancer
  - deploy a solution using `Cloud Marketplace`
    - browse `Cloud Marketplace` catalog
    - view solution details
    - deploy a `Cloud Marketplace` solution
- Deploy application infrastructure using `Cloud Deployment Manager`
  - develop `Deployment Manager templates`
  - launch `Deployment Manager templates`

### Ensure successful operation of a cloud solution

- Manage compute Engine resources
  - Manage a single `VM instance`
    - start
    - stop
    - edit configuration
    - delete and instance
  - `SSH/RDP` to the instance
  - Attach a GPU to a new instance and installig `CUDA libraries`
  - View current running `VM Inventory`
  - Work with `Snapshots`, `Images`
    - create Snapshot from a VM
    - create Image from VM or snapshot
    - view
    - delete
  - Work with `instance groups`
    - autoscaling parameters
    - assign instance template
    - create instance template
    - remove instance group
  - Work with management interfaces
    - `Cloud Console`
    - `Cloud Shell`
    - `GCloud SDK`
- Manage `Google Kubernetes Engine` resources
  - View current running `cluster inventory`
    - `nodes`
    - `pods`
    - `services`
  - Browse `container image repository` and view `container image details`
  - Work with `node pools`, `pods`, `services`
    - add
    - edit
    - remove
  - Work with `stateful applications`
    - `persistent volumes`
    - `stateful sets`
  - Work with management interfaces
    - `Cloud Console`
    - `Cloud Shell`
    - `GCloud SDK`
- Manage `App Engine` and `Cloud Run` resources
  - Adjust application `traffic splitting` parameters
  - Set `scaling parameters` for `autoscaling instances`
  - Work with management interfaces
    - `Cloud Console`
    - `Cloud Shell`
    - `GCloud SDK`
- Manage `storage and database solutions`
  - Move objects between `Cloud Storage` buckets
  - Convert `Cloud Storage`buckets between storage classes
  - Set `object life cycle management` policies for `Cloud Storage` buckets
  - Execute queries to retrieve data from data instances
  - Estimate costs of `BigQuery` query
  - Back up and restore data instances
    - `Cloud SQL`
    - `Cloud Datastore`
  - Review job status in `Cloud Dataproc`, `Cloud Dataflow`, or `BigQuery`
  - Work with management interfaces
    - `Cloud Console`
    - `Cloud Shell`
    - `GCloud SDK`
- Manage `networking resources`
  - Add a subnet to an existing VPC
  - Expand a subnet to have more IP addresses
  - Reserve static external or internal IP address
  - Work with management interfaces
    - `Cloud Console`
    - `Cloud Shell`
    - `GCloud SDK`
- Monitoring and Logging
  - Create `Stackdriver` alerts based on resource metrics
  - Create `Stackdriver` custom metrics
  - Configure `log sinks` to export logs to external systems
    - on-premises
    - BigQuery
  - View and filtering logs in `StackDriver`
  - View specific log message in `StackDriver`
  - Use `cloud diagnostics` to researchan application issue
    - view `Cloud Trace` data
    - use `Cloud Debug` to view an application point-in-time
  - View `Google Cloud Platform` status
  - Work with management interfaces
    - `Cloud Console`
    - `Cloud Shell`
    - `GCloud SDK`


### Configure access and security

- Manage `identity and access management (IAM)` 
  - view IAM role assignments
  - assign IAM roles to accounts of Google Groups
  - define custom IAM roles
- Manage `service accounts` 
  - manage service accounts with limited privileges
  - assign a service account to VM instances
  - grant access to a service account in another project
- View `audit logs` for projects and manages services