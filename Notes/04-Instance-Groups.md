# Instance Groups and Templates

## Unmanaged Instance Group

- a collection of **heterogeneous VM instances** that you can add or substract from.
  - must be in the same zone
- very limited feature
- no auto scalling, health checks, rolling updates etc
- for a group of instances you want to manage yourself

### Creating Unmanged Instance Group

- GCP Navigation Menu > Compute Engine > Instance Groups
- Create Instance Group > New Unmanaged Instance Group
- Input details on:
  - Name
  - Location
  - Zone
- Select VM Instances
- Click `Create`

## Instance Templates

- used in creating Managed Instance Group
- defines specifications of VMs in Managed Instance Group
  - machine-type
  - boot dsik
  - service account
  - access scopes
- global resources
  - no need to specify region/zone

### Creating Instance Templates

- GCP Navigation Menu > Compute Engine > Instance Templates > Create Instance Template

## Managed Instance Group

- can be regional and have multiple zones

### Creating Managed Instance Group

- GCP Navigation Menu > Compute Engine > Instance Groups
- Create Instance Group > New Managed Instance Group
- configure region and zones
- configure instance template and auto-scaling option
  - CPU utilization
  - cooldown period
  - max/min number of instances