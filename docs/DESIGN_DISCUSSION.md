# Design Discussion - terraform-azure-landing-zone

Priya: I think we should keep this simple - go + K8s, get it shipping. We can add the fancy stuff later.

Marcus: Yeah but if we don't add metrics/alerts day 1, we'll get paged with zero visibility. Seen that before.

Priya: Fair. Ok, Prometheus + health probes in v0.1, tracing in v0.2?

Marcus: Deal. Also non-root container from the start - security team will block us otherwise.

Priya: Ship it.
