# Google Kubernetes Engine

docker build . -t asia.gcr.io/[projectid]/hello-node:1.0

## Steps

1. Upload to Google Container Registry
2. Create a Cluster. Deploy application in a pod and expose it using a service
3. Manually scale our cluster by increasing the node pool and pod size

## Deploying an Application to the Google Kubernetes Engine

1. Upload the application to Google Container Registry
2. Create a cluster and deploy the application

### Upload to Google Container Registry

- **asia.gcr.io** is the registry name

```cli
# Enable Google Container Registry API first
gcloud services enable containerregistry.googleapis.com

docker build . -t asia.gcr.io/[PROJECT_ID]/[APP_NAME]:[VERSION]

docker push asia.gcr.io/[PROJECT_ID]/[APP_NAME]

# Check if the the container is pushed
gcloud container images list --repository=asia.gcr.io/[PROJECT_ID]
```

### Create a Cluster and Deploy the Application

```cli
# set project configuration for compute region and zone

gcloud container clusters create [CLUSTER_NAME]

# get credentials for kubectl
gcloud container clusters get-credentials [CLUSTER_NAME]

# run application in the cluster
kubectl run [APP_NAME] --image asia.gcr.io/[PROJECT_ID]/[APP_NAME]:[VERSION]

# check pods running in cluster
kubectl get pods

# expose the cluster with a load balancer
# --port = port to access the pods
# --target-port = port exposed on the pods
# * traffic will flow from port 80 load  balancer into port 8080 in a pod
# --type = type of service to expose pods
kubectl expose deployment [APP_NAME] --port=80 --target-port=8080 --type=LoadBalancer

# wait for services to launch and get external IP
kubectl get services --watch
```

### Manually Scale Cluster

- **node pools** are a group of nodes within a cluster what have the same configuration
- **default node pool** is the initial node pool created when the cluster was initialized

```cli
# inspect current node pool in [APP_NAME]
gcloud container node-pools list --cluster [CLUSTER_NAME]

# check number of nodes in node pool
gcloud container node-pools describe [default-pool/NODE_POOL_NAME] --cluster [CLUSTER_NAME] | grep initialNodeCount

# increase the size of nodes
gcloud container clusters resize [CLUSTER_NAME] --node-pool [NODE_POOL_NAME] --num-node [5]

# increase number of pods
kubectl scale --replicas [3] deployment [APP_NAME]
```

## Deleting a Cluster

### Delete services

```cli
kubectl delete services [APP_NAME]
```

### Delete 

```cli
kubectl delete pod [POD_NAME]
```

### Delete Cluster

```cli
gcloud container clusters delete [CLUSTER_NAME]
```
