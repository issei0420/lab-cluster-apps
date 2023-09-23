# Kafka
This Kustomize project installs Strimzi Kafka.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
helm template strimzi-cluster-operator oci://quay.io/strimzi-helm/strimzi-kafka-operator \
    -n kafka \
    --values base/values.yaml \
    > base/manifests.yaml
```
