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