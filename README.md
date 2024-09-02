# k8s-dns

## Check DNS Resolution:
```
kubectl exec -it test -- nslookup web-service
```
## Test HTTP Connection:
```
kubectl exec -it test -- curl http://web-service
```
