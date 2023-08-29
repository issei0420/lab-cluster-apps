# Prometheus
This Kustomize project installs prometheus.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that prometheus-community helm repo is added.
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

# generate template
helm template prometheus -n monitoring --create-namespace prometheus-community/kube-prometheus-stack --values base/values.yaml > base/manifests.yaml
```
