# Enabling Private Google Access for a Subnet

## Steps

1. Create VPC network with disabled private access
2. VM Instance with no public IP

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

### Create VM Instance with no Public IP

```cli
gcloud compute instances create [INSTANCE_NAME] --network [NETWORK_NAME] --subnet [SUBNET_NAME] --zone [ZONE] --no-address
```