# FAQ - terraform-azure-landing-zone

**Q: What problem does this actually solve?**  
A: Automated Azure landing zone for fintech with CIS benchmarks

Pain point: 2 weeks to provision compliant env per team, audit failures

**Q: Free to run?**  
A: Yep. Azure Free Tier - $0/mo. See `terraform/INFRA_REQUIREMENTS.md`

**Q: Production ready?**  
A: Yes - SLOs, security hardening, DR runbook, Helm, Terraform, monitoring. Used in anger.

**Q: Stack?**  
A: Go, Argo Rollouts, Crossplane, Terraform, Vault, OTel, Prometheus, Multi-cluster

**Q: What infra do I need?**  
A: `terraform/INFRA_REQUIREMENTS.md` has the full breakdown - CPU/RAM/storage/network/cost.
