# OpenTelementry Collector
This Kustomize project installs open telemetry collector in given mode.

Apply one of the following with Kustomize.
- `deployment`: `./overlays/deployment`
- `daemonset`: `./overlays/daemonset`
- `sidecar`: `./overlays/sidecar`
- `dev`: `./overlays/dev`

## Generate manifests for dev
```sh
# Add repo
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts

# Generate manifests
helm template otelcollector-collector open-telemetry/opentelemetry-collector \
    -n monitoring \
    --values overlays/dev/values.yaml \
    > overlays/dev/manifests.yaml
```
