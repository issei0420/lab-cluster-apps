# OpenTelementry Collector
`dev` version of otel collector is used by the development environment for [the-bench](https://github.com/hanapedia/the-bench)
```sh
# Add repo
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts

# Generate manifests
helm template otelcollector-collector open-telemetry/opentelemetry-collector \
    -n monitoring \
    --values base/values.yaml \
    > base/manifests.yaml
```
