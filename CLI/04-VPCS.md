# Creating VPCs in GCP

Navigation Menu > Networking section > VPC network > VPC networks

## Auto Subnet Mode

The default network (which is automatically created for every project) already has subnet for all regions.

1. Click `Create a VPC Network` Button.
2. Enter VPC Name.
3. Choose `Automatic` in the Subnet Creation Mode.
    - all the subnets it will create for each region and their automated CIDR block range
4. Click `Create`

## Custom Mode

1. Click `Create a VPC Network` Button.
2. Enter VPC Name.
3. Choose `Custom` in the Subnet Creation Mode.
    - all the subnets it will create for each region and their automated CIDR block range
4. Enter the following details
    - Subnet Name
    - Region
    - IP Address Range
5. Click `Add Subnet`
6. Click `Create`

## Using CLI

<https://cloud.google.com/sdk/gcloud/reference/compute/networks>

### Create VPC network

``` cli
gcloud compute networks create [VPC_NAME] --subnet-mode [custom/auto] --description [DESCRIPTION]
```

### Create Subnet

```cli
gcloud compute networks subnets create [SUBNET_NAME] --network [VPC_NAME] --range [CIDR] --region [REGION]
```

### Create Firewall

``` cli
gcloud compute firewall-rules create [FIREWALL_NAME] --network [VPC_NAME] --allow tcp:22,icmp
```