# Chaos Mesh
This Kustomize project installs Chaos Mesh.

The maninfests are generated using `helm template` and then applied via Kustomize.

## Generate manifests
```sh
# make sure that chaos mesh helm repo is added.
helm repo add chaos-mesh https://charts.chaos-mesh.org
helm repo update

# generate template for containerd
helm template chaos-mesh --namespace chaos-mesh chaos-mesh/chaos-mesh --values overlays/containerd/values.yaml > overlays/containerd/manifests.yaml

# generate template for crio
helm template chaos-mesh --namespace chaos-mesh chaos-mesh/chaos-mesh --values overlays/crio/values.yaml > overlays/crio/manifests.yaml
```
