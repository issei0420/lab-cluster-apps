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
|OpenEBS|openebs/base|Kustomize|2|OpenEBS Installation|
|SealedSecret|sealed-secret/base|Kustomize|2|SealedSecret Installation|
|MinIO|minio/base|Kustomize|3|MinIO Installation|
|Prometheus|prometheus/base|Kustomize|4|Prometheus Installation|
|Grafana|grafana/base|Kustomize|4|Grafana Installation|
|saiki-tenant|tenant/overlays/saiki|Kustomize|5|Tenant used by Saiki san|
