# Google Kubernetes Engine

## Steps

1. Upload to Google Container Registry
2. Create a Cluster. Deploy application in a pod and expose it using a service
3. Manually scale our cluster by increasing the node pool and pod size

## Deploying an Application to the Google Kubernetes Engine

1. Upload the application to Google Container Registry
2. Create a cluster and deploy the application

### Upload to Google Container Registry

<https://cloud.google.com/sdk/gcloud/reference/container/clusters/create>

- **asia.gcr.io** is the registry name

```cli
# Enable Google Container Registry API first
gcloud services enable containerregistry.googleapis.com

docker build . -t asia.gcr.io/[PROJECT_ID]/[APP_NAME]:[VERSION]

docker push asia.gcr.io/[PROJECT_ID]/[APP_NAME]

# Check if the the container is pushed
gcloud container images list --repository=asia.gcr.io/[PROJECT_ID]
```

### Create a Cluster and Deploy the Application using CLI

<https://cloud.google.com/sdk/gcloud/reference/container/clusters/create>

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

<https://cloud.google.com/sdk/gcloud/reference/container/node-pools>

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

### Creating a Pod and opening a Bash Shell

```cli
kubectl run -it --rm utils --image=gcr.io/google-containers/ubuntu-slim:0.14 bash
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

## Create a Cluster and Deploy the Application using Console

GCP Navigation Menu > Kubernetes Engine > Clusters > Create Cluster

- Cluster Details
  - cluster name
  - location type: zonal
- Node Pools -> default pool
  - set node size
- Features
  - Telemetry > Enable Kubernetes Engine Monitoring
- Click Create

## Inspecting Kubernetes Events

- shows insights happening inside the cluster
  - differents status in node pools

```cli
kubectl get events
```

### Console

Kubernetes Engine > Workloads > [APP_NAME] > Events

## Inspecting Logs

``` cli
kubectl logs pod/[POD_NAME]
```

### Console

Kubernetes Engine > Workloads > [APP_NAME] > Managed Pods > [POD_NAME] > Logs > Container Logs > Log Viewer

## Cloud Monitoring

GCP Navigation Menu > Operations Section > Monitoring > Cloud Monitoring Workspace

Dashboards > Kubernetes Engine > 

- Infrastructure
  - general overview of clusters, pods, CPU & Memory metrics
- Workloads
  - filters workload for each cluster
- Services
  - views services

## Deploying Apps using a Configuration File

- yml file
- headless service - clusterIP: None

``` cli
kubectl apply -f [CONFIG_NAME].yml
```

``` yaml
# service section
apiVersion: v1
kind: Service
metadata:
  name: headless-nginx-service
  labels:
    app: nginx
spec:
  ports:
  - port: 80
    name: web
  clusterIP: None # declares this is a headless service
  selector:
    app: nginx
---
#StatefulSet section
apiVersion: apps/v1
kind: StatefulSet # declares this is a StatefulSet
metadata:
  name: web
spec:
  selector:
    matchLabels:
      app: nginx # Label selector that determines which Pods belong to the StatefulSet
                 # Must match spec: template: metadata: labels
  serviceName: "headless-nginx-service"
  replicas: 3
  template:
    metadata:
      labels:
        app: nginx # Pod template's label selector
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
          name: web
        volumeMounts: # decalres the use of persistent storage
        - name: www
          mountPath: /usr/share/nginx/html
  volumeClaimTemplates: # automatically generates external volume used by the container
  - metadata:
      name: www
    spec:
      accessModes: [ "ReadWriteOnce" ]
      resources:
        requests:
          storage: 1Gi
```
