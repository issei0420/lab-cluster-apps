# Lab Cluster Apps
This project contains ArgoCD manifests to provision applications running on [lab-cluster](https://github.com/hanapedia/lab-cluster) 

## Applications
All the applications are deployed using kustomize project found in `argo-conf` directory.

List of the applications deployed are:

| Name | Path | Type | Wave | Description |
|------|------|------|------|-------------|
|OpenEBS CRD|openebs/crd/base|Kustomize|1|OpenEBS CRD Installation|
|SealedSecret CRD|sealed-secret/crd/base|Kustomize|1|SealedSecret CRD Installation|
|Prometheus CRD|prometheus-crd/base|Kustomize|1|Prometheus CRD Installation|
|Otel CRD|otel/crd|Kustomize|1|Otel CRD Installation|
<!-- |Linkerd CRD|linkerd/crd|Kustomize|1|Linkerd CRD Installation| -->
|Strimzi Kafka CRD|kafka/crd|Kustomize|1|Strimzi Kafka CRD Installation|
|Chaos Mesh CRD|chaos-mesh/crd|Kustomize|1|Chaos Mesh CRD Installation|
|OpenEBS|openebs/base|Kustomize|2|OpenEBS Installation|
|SealedSecret|sealed-secret/base|Kustomize|2|SealedSecret Installation|
|Registry|registry/overlays/lab-cluster|Kustomize|3|Registry Installation|
|MinIO|minio/base|Kustomize|3|MinIO Installation|
|Prometheus|prometheus/base|Kustomize|4|Prometheus Installation|
|Grafana Tempo|tempo/base|Kustomize|4|Grafana Tempo Installation|
|Otel Operator|otel/operator|Kustomize|4|Otel Operator Installation|
|Otel Collector|otel/collector|Kustomize|4|Otel Collector Installation|
|Grafana|grafana/base|Kustomize|4|Grafana Installation|
<!-- |Linkerd Control Plane|linkerd/linkerd|Kustomize|4|Linkerd Control Plane Installation| -->
|Chaos Mesh|chaos-mesh/chaos-mesh|Kustomize|4|Chaos Mesh Installation|
<!-- |Linkerd Viz|linkerd/linkerd-viz|Kustomize|5|Linkerd Viz Installation| -->
|Strimzi Kafka|kafka/kafka|Kustomize|5|Strimzi Kafka Installation|
<!-- |saiki-tenant|tenant/overlays/saiki|Kustomize|5|Tenant used by Saiki san| -->
