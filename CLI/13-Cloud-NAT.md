# Creating NAT resource

## Cloud Router

- pre-requisite for NAT Gateway
- used to exhange routes between VPC and and on-premise network
- Cloud NAT uses Cloud Route for the purpose of grouping NAT configuration information

## Steps

1. Create VPC network and subntet
2. Create VM with no public IP
3. Create Cloud NAT

## Create VPC network

```cli
gcloud compute networks create [NETWORK_NAME] --subnet-mode custom
```

```cli
gcloud compute networks subnets create [SUBNET_NAME] --network [NETWORK_NAME] --region [REGION] --range [CIDR] --enable-private-ip-google-access
```

```cli
gcloud compute firewall-rules create allow-ssh-private-net --network [NETWORK_NAME] --allow tcp:22
```

```cli
gcloud compute firewall-rules create allow-internal-private-net --network [NETWORK_NAME] --allow tcp:1-65535,udp:1-65535,icmp --source-ranges 10.0.1.0/24
```

## Create VM Instance with no Public IP

```cli
gcloud compute instances create [INSTANCE_NAME] --network [NETWORK_NAME] --subnet [SUBNET_NAME] --zone [ZONE] --no-address
```

## Create Cloud NAT

GCP Navigation Menu > Networking Section > Network Services > Cloud NAT > Get Started > Create a NAT Gateway

- Enter details
  - gateway name
  - vpc network
  - region
- Create a Cloud Router
  - enter router name
- Click create
