# Strimzi Kafka CRD
This Kustomize project installs CRDs for strimzi kafka.

## Generate CRD files
The following command will retrieve the CRD from helm chart, extract only CRD manifests, then removes description fields
to circumvent the issue posted [here](https://github.com/openebs-community/helm-charts/issues/1500).

```sh
helm template strimzi-cluster-operator oci://quay.io/strimzi-helm/strimzi-kafka-operator --include-crds \
    | yq e 'select(.kind == "CustomResourceDefinition")' \
    | yq e 'del(.. | .description?)' \
    > base/crds.yaml
```
