# Install Linkerd CRD

Add repos
``` sh
# To add the repo for Linkerd stable releases:
helm repo add linkerd https://helm.linkerd.io/stable
helm repo update
```

Install CRDs
```sh
helm template linkerd-crds linkerd/linkerd-crds \
    -n linkerd --create-namespace \
    > crd.yaml
```
