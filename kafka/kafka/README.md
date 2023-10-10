# Kafka
This Kustomize project installs Strimzi Kafka.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests for dev
```sh
curl "https://strimzi.io/examples/latest/kafka/kafka-persistent-single.yaml" > overlays/dev/manifests.yaml
```
