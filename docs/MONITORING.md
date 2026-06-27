# Monitoring

- Prometheus scrapes `/metrics` every 15s
- Grafana dashboard: `monitoring/grafana-dashboard.json`
- Alerts:
  - HighErrorRate
  - PodCrashLoop
  - HighLatency p95 > 250ms

SLO: 99.9% availability, p95 < 250ms  
Error budget: 43m/month

Logs → Loki, Traces → Tempo / OTel
