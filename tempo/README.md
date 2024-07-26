# Grafana Tempo
This Kustomize project installs Grafana Tempo.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that openebs helm repo is added.
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# generate template
helm template tempo --namespace monitoring grafana/tempo-distributed --values distributed/values.yaml > distributed/manifests.yaml
```
