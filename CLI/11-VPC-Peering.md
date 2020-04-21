# VPC Peering

<https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings>

## Notes

- IP address range of VPC subnets should not overlap

## Creating Peering Connection

<https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/create>

- Create on all/both vpc networks

``` cli
gcloud compute networks peerings create [PEER_NAME] --network [VPC_NAME_1] --peer-network [VPC_NAME_2] --auto-create-routes
```

- --auto-create-routes
  - If set, will automatically create routes for the network peering. Note that a backend error will be returned if this is not set

## Getting Network and Subnet ID

gcloud compute networks describe [NETWORK_NAME] | grep id

gcloud compute networks subnets describe [SUBNET_NAME] --region [REGION] | grep id 