# terraform-azure-landing-zone

> Automated Azure landing zone for fintech with CIS benchmarks

**Domain:** devops | **Complexity:** expert | **Stack:** Go, Argo Rollouts, Crossplane, Terraform, Vault, OTel, Prometheus, Multi-cluster

| | |
|---|---|
| Use case | Automated Azure landing zone for fintech with CIS benchmarks |
| Pain point | 2 weeks to provision compliant env per team, audit failures |
| Success metric | Env provision 14d → 25min, 100% CIS pass |
| Cost | $0/mo on Azure Free Tier |

## Why this exists

2 weeks to provision compliant env per team, audit failures. Automated Azure landing zone for fintech with CIS benchmarks

## Quick start

```bash
docker build -t terraform-azure-landing-zone:local .
docker run -p 8080:8080 terraform-azure-landing-zone:local
curl http://localhost:8080/healthz
```

## Architecture

```
GitHub CI -> GHCR -> K8s -> Prometheus -> Grafana
     ^                         |
   FluxCD <--------------------+
```

See `docs/ARCHITECTURE.md`

## Infrastructure

Full spec: `terraform/INFRA_REQUIREMENTS.md`

TL;DR: K8s cluster, 2-10 pods HPA, $0 on Azure Free Tier

## Docs

- `docs/ARCHITECTURE.md` - components, tradeoffs
- `docs/DESIGN_DISCUSSION.md` - how we decided to build this
- `docs/DEPLOYMENT.md` - GitOps, rollback
- `docs/SECURITY.md` - threat model
- `docs/TROUBLESHOOTING.md` - 3am runbook
- `terraform/INFRA_REQUIREMENTS.md` - **infra: CPU/RAM/storage/cost**

Interview prep: `interview/`
