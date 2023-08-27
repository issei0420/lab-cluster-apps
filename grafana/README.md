# Grafana
This Kustomize project installs Grafana.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that grafana helm repo is added.
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# generate template
helm template grafana -n monitoring --create-namespace grafana/grafana --values base/values.yaml > base/manifests.yaml
```
