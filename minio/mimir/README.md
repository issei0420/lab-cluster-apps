## MinIO deployment for Grafana Mimir storage

### Generate secrets
```sh
# Mimir
# generate secrets from files for mimir
k create secret generic minio-mimir \
  --namespace monitoring \
  --from-file=rootUser=secrets/rootUser \
  --from-file=rootPassword=secrets/rootPassword \
  --dry-run=client -o yaml > secrets/mimir-raw-admin-secret.yaml

# seal the secrets
kubeseal -o yaml < secrets/mimir-raw-admin-secret.yaml > mimir-sealed-admin-secret.yaml

```

### Generate other manifests
```sh
helm template minio --namespace monitoring --create-namespace minio/minio --values values.yaml > manifests.yaml
```
