# k8s-dns

## Check DNS Resolution:
```
kubectl exec -it test -- nslookup web-service
```
## Test HTTP Connection:
```
kubectl exec -it test -- curl http://web-service
```
## Testing Cross-Namespace Access (web-service.apps):
- For cross-namespace access, you need to specify the service name along with the namespace. From the test pod in the default namespace, run:
```
curl http://web-service.apps
curl http://web-service.apps.svc
```

# Kubernetes Service Table

This table provides information about the Kubernetes services and their DNS resolution.

| Hostname     | Namespace | Type | Root         | IP Address    |
|--------------|-----------|------|--------------|---------------|
| web-service  | apps      | svc  | cluster.local| 10.107.37.188 |

## Description of Table Columns:

- **Hostname**: The name of the service within the Kubernetes cluster.
- **Namespace**: The Kubernetes namespace in which the service resides (e.g., `apps`).
- **Type**: Indicates the resource type (e.g., `svc` for service).
- **Root**: The root domain used within the Kubernetes cluster (default is `cluster.local`).
- **IP Address**: The internal cluster IP address of the service.

