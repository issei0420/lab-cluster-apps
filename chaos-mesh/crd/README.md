# Chaos Mesh CRD
This Kustomize project installs CRDs for chaos mesh.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/openebs-community/helm-charts/issues/1500).
```sh
helm template chaos-mesh chaos-mesh/chaos-mesh --include-crds \
    | yq e 'select(.kind == "CustomResourceDefinition")' \
    | yq e 'del(.. | .description?)' \
    > base/crds.yaml
```
