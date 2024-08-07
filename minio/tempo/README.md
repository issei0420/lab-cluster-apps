## MinIO deployment for Grafana Tempo storage

### Generate secrets
```sh
# Tempo
# generate secrets from files for tempo
k create secret generic minio-tempo \
  --namespace monitoring \
  --from-file=rootUser=secrets/rootUser \
  --from-file=rootPassword=secrets/rootPassword \
  --dry-run=client -o yaml > secrets/tempo-raw-admin-secret.yaml

# seal the secrets
kubeseal -o yaml < secrets/tempo-raw-admin-secret.yaml > tempo-sealed-admin-secret.yaml
```

### Generate other manifests
```sh
helm template minio --namespace monitoring --create-namespace minio/minio --values values.yaml > manifests.yaml
```
