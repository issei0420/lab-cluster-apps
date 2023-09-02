# Cert Manager
This Kustomize project installs cert manager.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that cert-manager helm repo is added.
helm repo add jetstack https://charts.jetstack.io
helm repo update

# generate template
helm template cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --values base/values.yaml > base/manifests.yaml
```
