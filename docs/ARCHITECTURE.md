# Architecture - terraform-azure-landing-zone

> Automated Azure landing zone for fintech with CIS benchmarks

**Pain:** 2 weeks to provision compliant env per team, audit failures  
**Success metric:** Env provision 14d → 25min, 100% CIS pass

## Decision log

We chose K8s + go because the team already runs 40 services on K8s. Serverless would be cheaper at low scale but vendor lock-in wasn't worth it for this.

See `docs/architecture/ADR-001-runtime-choice.md`

## Components

- go service, Prometheus metrics, /healthz /readyz
- Docker distroless, non-root
- K8s Deployment + HPA 2-10, 70% CPU
- GitOps (FluxCD)
- Prometheus + Grafana

## Trade-offs

| Choice | Why | Cost |
|---|---|---|
| K8s over serverless | team expertise, portability | more YAML |
| Prometheus self-hosted | $0 vs $800/mo Datadog | we run it |
| RollingUpdate vs Canary | simpler for v0.1, canary in v0.2 | faster ship |

## Data flow

```
Client -> Ingress -> Service -> Pod
Pod -> /metrics -> Prometheus -> Alertmanager -> Slack
Logs -> stdout -> Loki
```

## Scaling

HPA 2-10 pods. Stateless. 50m/64Mi request.

## Why not...

- **Serverless?** Cold start would kill our p95. Also, team knows K8s.
- **Managed Prometheus?** $400/mo. We run kube-prometheus for $0.
