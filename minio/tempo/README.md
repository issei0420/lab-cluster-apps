## MinIO deployment for Grafana Tempo storage

### Generate other manifests
```sh
helm template minio --namespace monitoring --create-namespace minio/minio --values values.yaml > manifests.yaml
```
