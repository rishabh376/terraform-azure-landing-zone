# Setup - terraform-azure-landing-zone

Automated Azure landing zone for fintech with CIS benchmarks

1. **Infra first**: `cd terraform && terraform init && terraform apply`
   Full spec in `terraform/INFRA_REQUIREMENTS.md`
2. `kubectl apply -k k8s/ -n terraform-azure-landing-zone`
3. `kubectl port-forward svc/terraform-azure-landing-zone 8080:80 -n terraform-azure-landing-zone`
4. `curl localhost:8080/healthz`

Env vars: `PORT=8080`, `LOG_LEVEL=info`
