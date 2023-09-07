# Install Linkerd
## Installing Control Plane
Prerequisite: generate identity certificates for root certificate for mTLS

*requires `step`*
*requires crd installation
*requires cert manager

Generate Trust anchor cert
```sh
cd base/secrets
# generate cert and key
step certificate create root.linkerd.cluster.local ca.crt ca.key \
--profile root-ca --no-password --insecure --not-after 87600h

# dry-run to create secret yaml
kubectl create secret tls linkerd-trust-anchor --dry-run=client \
        --cert=ca.crt \
        --key=ca.key \
        --namespace=linkerd \
        -o yaml > certs.yaml

cd ..

# seal the secret
kubeseal -o yaml < secrets/certs.yaml > sealed-certs.yaml
```

Generate Control Plane manifests with ca.crt inserted
```sh
# generate manifests
helm template linkerd-control-plane -n linkerd \
    --set identity.issuer.scheme=kubernetes.io/tls \
    --set identityTrustAnchorsPEM=$(cat secrets/ca.crt)\
    linkerd/linkerd-control-plane \
    > manifests.yaml
```
