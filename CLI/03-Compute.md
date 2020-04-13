# CLI commands for GCP Compute Resources

## Compute Engine

``` cli
List all Compute Instances

$ gcloud compute instances list


Create Compute Engine Resource

$ gcloud compute instances create [INSTANCE_NAME] --network=[VPC-name] --subnet=[SUBNET-name] --zone=[ZONE]


Show properties
Instance-ID, tags

$ gcloud compute instances describe [INSTANCE_NAME]


Delete Compute Instance

$ gcloud compute instances delete [INSTANCE_NAME]


Add tags

$  gcloud compute instances add-tags [INSTANCE_NAME] --tags=[TAG1,TAG2] --zone=[ZONE]
```
