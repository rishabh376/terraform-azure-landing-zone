# Operations Runbook - terraform-azure-landing-zone

Automated Azure landing zone for fintech with CIS benchmarks

**On-call? Read this first.**

## Deploy
```
kubectl apply -k k8s/ -n terraform-azure-landing-zone
kubectl rollout status deploy/terraform-azure-landing-zone -n terraform-azure-landing-zone
```

## Rollback (when things go red)
```
./scripts/rollback.sh
# usually < 30sec
```

## Scale up NOW
```
kubectl scale deploy/terraform-azure-landing-zone --replicas=10 -n terraform-azure-landing-zone
```

## Logs
```
kubectl logs -l app=terraform-azure-landing-zone -n terraform-azure-landing-zone -f --tail=200
```

## Crashloop?
```
kubectl describe pod -l app=terraform-azure-landing-zone -n terraform-azure-landing-zone
kubectl logs <pod> --previous -n terraform-azure-landing-zone
```
90% of the time: missing env var in ConfigMap.

## Metrics
`curl localhost:8080/metrics` or Grafana dashboard in `monitoring/`

## DR / Failover
See `docs/DISASTER_RECOVERY.md` - RTO 15m

We actually tested this. 11 min.
