# Configure SSH Access to Compute Engine using Firewall Rules

## Outline

1. Create a new VPC with a custom subnet
    - default VPC network has pre-configured firewalls
2. Create a compute instance to connect to
3. Crate firewall-rules to allow SSH connection from anywhere
4. Connect to our compute instance using SSH

## Implied Firewall Rules

1. Implied ALLOW egress rule
    - Allow any outgoing requests to any destination
2. Implied DENY ingress rule
    - Deny all incoming requests using what ever protocol from whatever source

### Implied Priority

Firewall-rules priority is from **0 to 65535**.
Implied Rules have an implied priority of **65535**, lowest priority.

If a priority is not specified, the default value is **1000**

## Create a New VPC

Create a custom-mode subnet VPC. No subnets automatically created.

``` cli
$ gcloud compute networks create [VPC-name] --subnet-mode=custom
```

List VPC networks

``` cli
$ gcloud compute networks list
```

Create a Subnet
``` cli
$ gcloud compute networks subnets create [SUBNET-name] \
--network=[VPC-name] \
--region=asia-east1 \
--range=10.1.0.0/16
```

Check VPC's firewall-rules

``` cli
$ gcloud compute firewall-rules list --filter NETWORK=practice-network
```

## Create Compute Instance

Create compute instance in the network created

``` cli
$ gcloud compute instances create [INSTANCE_NAME] --network=[VPC-name] --subnet=[SUBNET-name] --zone=[ZONE]
```

Create tags as target of firewall rule

```cli
$ gcloud compute instances add-tags [INSTANCE_NAME] --tags=[TAG1,TAG2] --zone=[ZONE]
```

Check if tags are associated to the instance

``` cli
$ gcloud compute instances describe [INSTANCE_NAME]
```

## Create a Firewall-Rule to allow SSH

``` cli
$ gcloud compute firewall-rules create [FIRERULE_NAME] \
--network=[VPC_NAME] \
--allow=tcp:22 \
--direction=INGRESS \
--source-ranges=0.0.0.0/0 \
--target-tags=[TAG]
```

SSH to compute instance

``` cli
$ gcloud compute ssh [INSTANCE_NAME] --zone=[ZONE]
```

## Create a Firewall-Rule to allow HTTP

``` cli
$ gcloud compute firewall-rules create [FIRERULE_NAME] \
--network=[VPC_NAME] \
--allow=tcp:80 \
--direction=INGRESS \
--source-ranges=0.0.0.0/0 \
--target-tags=[TAG]
```