# MinIO
This Kustomize project installs MinIO.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that openebs helm repo is added.
helm repo add minio https://charts.min.io/
helm repo update

# generate template
helm template minio --namespace monitoring --create-namespace minio/minio --values base/values.yaml > base/manifests.yaml
```
