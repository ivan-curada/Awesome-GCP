# CLI Commands for Setting up Load Balancers

## Creating a regial TDP/UDP Network Load Balancer 

1. Attach instance/s to a target pool
2. Attach target pool to load balancer

### Target Pools

``` cli

Create target pool

$ gcloud compute target-pools create [NAME] --region=[REGION]


List created target-pool

$ gcloud compute target-pools list


Add an instance to a target pool

$ gcloud compute target-pools add-instances [TARGET_POOL_NAME] --instances [INSTANCE_NAME]
```

### TCP/UDP network load balancer

```cli
Create a TCP/UDP network load balancer

$ gcloud compute forwarding-rules create [NAME] --ports=80 --target-pool [TARGET_POOL_NAME] --region=[REGION]


List created load balancers

$ gcloud compute forwarding-rules list
```