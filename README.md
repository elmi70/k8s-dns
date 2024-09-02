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
