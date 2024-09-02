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
curl http://web-service.apps.svc.cluster.local
```

### Kubernetes DNS Resolution Table

| DNS Name                                      | Namespace | Resource Type | Root          | IP Address  |
|-----------------------------------------------|-----------|---------------|---------------|-------------|
| 10-244-1-2.default.pod.cluster.local          | default   | pod           | cluster.local | 10.244.1.2  |
| web-service.apps.svc.cluster.local            | apps      | service       | cluster.local | 10.100.30.140 |

#### Description of Table Columns:
- **DNS Name**: The fully qualified DNS name used to resolve the resource within the Kubernetes cluster.
  - For pods, it follows the format `POD-IP-NAME.NAMESPACE.pod.cluster.local`.
  - For services, it follows the format `SERVICE-NAME.NAMESPACE.svc.cluster.local`.
- **Namespace**: The Kubernetes namespace where the resource resides.
- **Resource Type**: The type of resource being resolved. This can be a `pod` or `service`.
- **Root**: The root domain for DNS resolution within the Kubernetes cluster, which is typically `cluster.local`.
- **IP Address**: The internal IP address associated with the resource.

#### Example Entries:
- **Pod**: The DNS name `10-244-1-2.default.pod.cluster.local` resolves to a pod with the IP address `10.244.1.2` in the `default` namespace.
- **Service**: The DNS name `web-service.apps.svc.cluster.local` resolves to a service with the IP address `10.100.30.140` in the `apps` namespace.


