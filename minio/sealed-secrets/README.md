## Sealed Secrets for admin user and password
The secrets are managed separately because adding prefix with kustomize makes the secrets unsealable.

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

