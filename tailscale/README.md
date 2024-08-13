## tailscale Operator

### Generate secrets
```sh
# MANUALLY create secret with following stringData in `tailscale` namespace and name it raw-operator-oauth.yaml
# client_id: <client id in secrets/client_id>
# client_secret: <client id in secrets/client_secret>

# seal the secrets
kubeseal -o yaml < secrets/raw-operator-oauth.yaml > operator-oauth.yaml
```
