# Cert Manager CRD
This Kustomize project installs CRDs for cert manager.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/prometheus-community/helm-charts/issues/1500).
```sh
wget https://github.com/cert-manager/cert-manager/releases/download/v1.12.0/cert-manager.crds.yaml -O base/crds.yaml
```
