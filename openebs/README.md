# OpenEBS
This Kustomize project installs OpenEBS.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that openebs helm repo is added.
helm repo add openebs https://openebs.github.io/charts
helm repo update

# generate template
helm template openebs --namespace openebs openebs/openebs --create-namespace --values base/values.yaml > base/manifests.yaml
```
