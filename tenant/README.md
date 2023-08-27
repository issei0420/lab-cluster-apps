# Tenant creation
This directory contains the following:
- Kustomize project to create tenant. It creates resources such as
    - Namespace
    - Role, RoleBinding
    - ClusterRole, ClusterRoleBinding
    - ResourceQuota
- Makefile to generate kubeconfig file for the user of the tenant.

## Usage
### Creating tenant
1. Define an overlay for the tenant by looking at example overlay, and apply it.
```sh
kubectl apply -k overlays/[new tenant overlay]
```

2. Create user for the tenant.
```sh
# generate cert files and CSR
make request USER_NAME= # name of user, use tenant name for clarity

# approve CSR
kubectl approve 

# generate kubeconfig with crt
make generate USER_NAME= # name of user, use tenant name for clarity
```

3. Remove generated files.
After securely sharing the kubeconfig, remove the generated certs for security measures.
```sh
make cleanup USER_NAME= # name of user, use tenant name for clarity
```

### Deleting tenant
Simply delete the resource created by kustomize.
```sh
kubectl delete -k overlays/[tenant overlay]
```

No action needed to delete the user as roles will be deleted.
