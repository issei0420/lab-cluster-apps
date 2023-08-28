# SealedSecret CRD
This Kustomize project installs CRDs for sealed secret.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/prometheus-community/helm-charts/issues/1500).
```sh
helm template sealed-secrets --namespace kube-system sealed-secrets/sealed-secrets --include-crds \
    | yq e 'select(.kind == "CustomResourceDefinition")' \
    | yq e 'del(.. | .description?)' \
    > base/crds.yaml
```
