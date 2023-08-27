# Variables
CLUSTER_NAME?=lab
API_SERVER=https://kubernetes:6443
CA_PATH?=lab-ca.crt
USER_NAME?=my-user
USER_CERT_PATH=./generated/$(USER_NAME).crt
USER_KEY_PATH=./generated/$(USER_NAME).key
USER_CSR_PATH=./generated/$(USER_NAME).csr
KUBE_CSR_PATH=./generated/$(USER_NAME)-csr.yaml
KUBECONFIG_PATH=./generated/$(USER_NAME)-$(CLUSTER_NAME).yaml
CONTEXT_NAME=$(USER_NAME)-$(CLUSTER_NAME)
NAMESPACE?=$(USER_NAME)
CSR_NAME=$(USER_NAME)-csr

# Make command to request a certificate
request:
	# Generate the private key and CSR
	@openssl genrsa -out $(USER_KEY_PATH) 2048
	@openssl req -new -key $(USER_KEY_PATH) -out $(USER_CSR_PATH) -subj "/CN=$(USER_NAME)/O=system:basic-user"
	# Use yq to replace placeholders in the CSR template and create a new YAML file
	@cat csr-template.yaml | \
	yq eval ".metadata.name = \"$(CSR_NAME)\"" - | \
	yq eval ".spec.request = \"$$(cat $(USER_CSR_PATH) | base64 | tr -d '\n')\"" - > $(KUBE_CSR_PATH)
	# Apply the modified YAML to the Kubernetes cluster
	@kubectl apply -f $(KUBE_CSR_PATH)

# Make command to generate the kubeconfig
generate:
	# Retrieve the signed certificate from the CSR
	@kubectl get csr $(CSR_NAME) -o jsonpath='{.status.certificate}' | base64 --decode > $(USER_CERT_PATH)
	# Generate the kubeconfig
	@kubectl config set-cluster $(CLUSTER_NAME) \
	  --server=$(API_SERVER) \
	  --certificate-authority=$(CA_PATH) \
	  --embed-certs=true \
	  --kubeconfig=$(KUBECONFIG_PATH)
	@kubectl config set-credentials $(USER_NAME) \
	  --client-certificate=$(USER_CERT_PATH) \
	  --client-key=$(USER_KEY_PATH) \
	  --embed-certs=true \
	  --kubeconfig=$(KUBECONFIG_PATH)
	@kubectl config set-context $(CONTEXT_NAME) \
	  --cluster=$(CLUSTER_NAME) \
	  --user=$(USER_NAME) \
	  --namespace=$(NAMESPACE) \
	  --kubeconfig=$(KUBECONFIG_PATH)
	@echo "Kubeconfig generated at $(KUBECONFIG_PATH)"

cleanup:
	# Deleting generated resources
	@rm $(KUBECONFIG_PATH)
	@rm $(USER_KEY_PATH)
	@rm $(USER_CERT_PATH)
	@rm $(USER_CSR_PATH)
	@rm $(KUBE_CSR_PATH)

.PHONY: request generate
