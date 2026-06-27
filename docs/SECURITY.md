# Security - terraform-azure-landing-zone

What we do:
- Trivy scan in CI - blocks HIGH/CRITICAL
- Cosign sign images
- Non-root UID 10001, readOnlyRootFilesystem
- NetworkPolicy default-deny
- RBAC least-privilege
- Secrets via External Secrets / Vault (not in git, obviously)
- Dependabot + CodeQL on

Threat model: STRIDE. Biggest risk is supply chain - hence Cosign + Trivy.

Seeing something? Open a security advisory, don't file a public issue please.
