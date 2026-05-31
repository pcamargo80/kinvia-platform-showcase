# Security

## Authentication Layer

Authelia is integrated with Traefik using forward authentication.

Current policy:

- One-factor authentication

Planned:

- Multi-factor authentication (MFA)
- Stronger access policies
- Identity hardening

## Protected Services

- Grafana
- Prometheus
- Loki
- Uptime Kuma

## Exposure Strategy

Public:

- kinvia.dev
- www.kinvia.dev
- auth.kinvia.dev

Restricted:

- grafana.kinvia.dev
- prometheus.kinvia.dev
- loki.kinvia.dev
- uptime.kinvia.dev

Internal Only:

- PostgreSQL
- Redis
- Node Exporter
- cAdvisor
- Promtail
- Traefik Dashboard

## Security Principles

- Least privilege
- Minimize attack surface
- Internal-only infrastructure services
- End-to-end HTTPS
- No direct database exposure
