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

## Configuration
### Adding Dashboards
1. Add the dashboard json file in `base/dashboards`.
2. If the file is too big, compress using 
```sh
jq -c . < big.json > compressed.json
```
3. add the file to the list in configMapGenerator for dashboards.

### Adding Data Sources
Almost same as dashboards except files are yaml.
