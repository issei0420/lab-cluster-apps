# SealedSecret
This Kustomize project installs SealedSecret.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that openebs helm repo is added.
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets
helm repo update

# generate template
helm template sealed-secrets --namespace kube-system sealed-secrets/sealed-secrets --values base/values.yaml > base/manifests.yaml
```
