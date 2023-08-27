# Prometheus CRD
This Kustomize project installs CRDs for kube-prometheus-stack.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/prometheus-community/helm-charts/issues/1500).
```sh
helm template prometheus -n monitoring --create-namespace prometheus-community/kube-prometheus-stack --include-crds \
    | yq e 'select(.kind == "CustomResourceDefinition")' \
    | yq e 'del(.. | .description?)' \
    > prometheus-crd/base/crds.yaml
```
