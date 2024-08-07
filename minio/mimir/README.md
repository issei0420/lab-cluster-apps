## MinIO deployment for Grafana Mimir storage

### Generate other manifests
```sh
helm template minio --namespace monitoring --create-namespace minio/minio --values values.yaml > manifests.yaml
```
