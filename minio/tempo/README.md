## MinIO deployment for Grafana Tempo storage

### Generate secrets
```sh
# generate secrets from files
k create secret generic minio-tempo \
  --from-file=rootUser=secrets/rootUser \
  --from-file=rootPassword=secrets/rootPassword \
  --dry-run=client -o yaml > secrets/raw-admin-secret.yaml

# seal the secrets
kubeseal -o yaml < secrets/raw-admin-secret.yaml > sealed-admin-secret.yaml
```

### Generate other manifests
```sh
helm template minio --namespace monitoring --create-namespace minio/minio --values values.yaml > manifests.yaml
```