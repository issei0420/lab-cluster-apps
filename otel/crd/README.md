# OpenTelemetry CRD
This Kustomize project installs CRDs for open-telemetry.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/prometheus-community/helm-charts/issues/1500).
```sh
helm template opentelemetry-operator open-telemetry/opentelemetry-operator --include-crds --values ../operator/base/values.yaml \
    | yq e 'select(.kind == "CustomResourceDefinition")' \
    | yq e 'del(.. | .description?)' \
    > base/crds.yaml
```
