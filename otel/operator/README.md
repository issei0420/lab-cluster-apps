# OpenTelementry Operator
This Kustomize project installs open telemetry operator.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that open telemetry helm repo is added.
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
helm repo update

# generate template
helm template opentelemetry-operator open-telemetry/opentelemetry-operator --values base/values.yaml > base/manifests.yaml
```
