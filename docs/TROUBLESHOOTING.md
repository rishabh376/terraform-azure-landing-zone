# Troubleshooting - terraform-azure-landing-zone

**CrashLoopBackOff**  
`kubectl logs deploy/terraform-azure-landing-zone -n terraform-azure-landing-zone --previous`  
Usually missing env var. Check the ConfigMap.

**ImagePullBackOff**  
GHCR auth secret expired. `kubectl create secret docker-registry ...`

**500s spiking**  
Check `/metrics`, then Prometheus alerts. Usually downstream timeout.

**Latency p95 high**  
`kubectl get hpa -n terraform-azure-landing-zone` - is it scaling? Check metrics-server.

**OOMKilled**  
Bump memory limit in `helm/terraform-azure-landing-zone/values.yaml`. Then find the leak.

**Flux won't sync**  
`flux get kustomizations` - usually git repo URL rotated.
