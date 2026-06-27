# Deployment - terraform-azure-landing-zone

**Use case:** Automated Azure landing zone for fintech with CIS benchmarks

## Infra requirements
→ `terraform/INFRA_REQUIREMENTS.md` - CPU/RAM/storage/network/cost breakdown

## GitOps
Flux watches `main`:
```
flux bootstrap github --owner=you --repository=terraform-azure-landing-zone
```

## Rollback
```
./scripts/rollback.sh
# or
kubectl rollout undo deploy/terraform-azure-landing-zone -n terraform-azure-landing-zone
```
Usually < 30sec.

## Cost
Azure Free Tier - $0/mo
