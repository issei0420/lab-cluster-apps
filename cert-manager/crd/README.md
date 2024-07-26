# Cert Manager CRD
This Kustomize project installs CRDs for cert manager.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/prometheus-community/helm-charts/issues/1500).
```sh

helm template cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --set crds.enabled=true \
    | yq e 'select(.kind == "CustomResourceDefinition")' \
    | yq e 'del(.. | .description?)' \
    > base/crds.yaml
```
