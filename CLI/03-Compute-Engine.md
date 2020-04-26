# CLI commands for GCP Compute Instance

<https://cloud.google.com/sdk/gcloud/reference#--configuration>



## Google Compute Engine

``` cli
List all Compute Instances

$ gcloud compute instances list
```

### Create Compute Engine Resource

<https://cloud.google.com/sdk/gcloud/reference/compute/instances/create>

```cli
$ gcloud compute instances create [INSTANCE_NAME] --network=[VPC-name] --subnet=[SUBNET-name] --zone=[ZONE] --machine-type [MACHINE_TYPE]
```

### Show properties

Instance-ID, tags

``` cli
$ gcloud compute instances describe [INSTANCE_NAME]
```

### Delete Compute Instance

```cli
$ gcloud compute instances delete [INSTANCE_NAME]
```

### Add tags

<https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-tags>

``` cli
$  gcloud compute instances add-tags [INSTANCE_NAME] --tags=[TAG1,TAG2] --zone=[ZONE]
```
