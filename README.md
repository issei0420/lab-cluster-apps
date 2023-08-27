# Lab Cluster Apps
This project contains ArgoCD manifests to provision applications running on [lab-cluster](https://github.com/hanapedia/lab-cluster) 

## Applications
All the applications are deployed using kustomize project found in `argo-conf` directory.

List of the applications deployed are:

| Name | Path | Type | Wave | Description |
|------|------|------|------|-------------|
|OpenEBS|openebs/base|Kustomize|1|OpenEBS Installation|
|Prometheus CRD|prometheus-crd/base|Kustomize|2|Prometheus CRD Installation|
|Prometheus|prometheus/base|Kustomize|3|Prometheus Installation|
|Grafana|grafana/base|Kustomize|3|Grafana Installation|
|saiki-tenant|tenant/overlays/saiki|Kustomize|5|Tenant used by Saiki san|
