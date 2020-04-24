# Kubernetes using Minikube

<https://kubernetes.io/docs/tasks/tools/install-minikube/>

<https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#apply>

## Steps

1. Start Minikube
2. Create a Deployment
3. Expose the Service
4. Check Pods
5. Get URL of the Service
6. Checkk Service URL
7. Delete the Service
8. Delete the Deployment
9. Stop Minikube
10. Delete Minikube cluster

### Start Minikube

```cli
sudo mv minikube /usr/local/bin
```

### Create a Deployment

```cli
kubectl create deployment [DEPLOYMENT_NAME] --image=k8s.gcr.io/echoserver:1.10 --context=minikube
```

### Expose the Service

```cli
kubectl expose deployment [DEPLOYMENT_NAME] --type=NodePort --port=8080 --context=minikube
```

### Check Pods

```cli
kubectl get pod
```

### Get URL of the Service

```cli
minikube service [DEPLOYMENT_NAME] --url
```

### Checkk Service URL

```cli
curl --include http://192.168.64.2:30327
```

### Delete the Service

```cli
kubectl delete services [DEPLOYMENT_NAME] --context=minikube
```

### Delete the Deployment

```cli
kubectl delete deployment [DEPLOYMENT_NAME] --context=minikube
```

### Stop Minikube

```cli
minikube stop
```

### Delete Minikube cluster

```cli
minikube delete
```
