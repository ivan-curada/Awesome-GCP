# Creating VPCs in GCP using the Console

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