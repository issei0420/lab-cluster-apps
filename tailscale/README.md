## tailscale Operator

### Generate secrets
```sh
# generate secrets from files for mimir
k create secret generic operator-oauth \
  --namespace tailscale \
  --from-file=clientId=secrets/client_id \
  --from-file=clientSecret=secrets/client_secret \
  --dry-run=client -o yaml > secrets/raw-operator-oauth.yaml

# seal the secrets
kubeseal -o yaml < secrets/raw-operator-oauth.yaml > operator-oauth.yaml
```
