# Installation - terraform-azure-landing-zone

You'll need: Docker, kubectl, Helm, Go 1.22+

```bash
git clone <repo>
cd terraform-azure-landing-zone
go test ./...
docker build -t terraform-azure-landing-zone:local .
```

Infra prerequisites: see `terraform/INFRA_REQUIREMENTS.md`
