### Deploy the Metrics Server with the following command
```yaml
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

### Verify that the metrics-server deployment is running the desired number of pods with the following command
```yaml
kubectl get deployment metrics-server -n kube-system
```

### to enable the metrics-server get pod details, add the resource name to the deployment
```yaml
resources:
   limits:
     cpu: 500m
   requests:
     cpu: 200m
```

### deploy secrets and config maps to eks-cluster configuration
```yaml
kubectl apply -f aws-secret.yaml
kubectl apply -f env-secret.yaml
kubectl apply -f env-configmap.yaml

```
### delete all pods, deployments and services from the eks cluster
```yaml
kubectl delete all --all
```

### deploy pods and services to eks cluster
```yaml
kubectl apply -f deployment/backend-user-deployment.yaml
kubectl apply -f deployment/backend-feed-deployment.yaml
kubectl apply -f service/backend-user-service.yaml
kubectl apply -f service/backend-feed-service.yaml
kubectl apply -f deployment/frontend-deployment.yaml
kubectl apply -f service/frontend-service.yaml
kubectl get pods
kubectl apply -f deployment/reverseproxy-deployment.yaml
kubectl apply -f service/reverseproxy-service.yaml
timeout 5
kubectl get pods
kubectl expose deployment udagram-frontend --type=LoadBalancer --name=frontend-ingress
timeout 5
kubectl expose deployment udagram-reverseproxy --type=LoadBalancer --name=reversproxy-ingress
timeout 5
kubectl get services
timeout 10
kubectl autoscale deployment udagram-api-feed --cpu-percent=50 --min=3 --max=5
```

### Connect to pod internal CLI
```yaml
kubectl exec --stdin --tty <pod-name> -- /bin/bash

```