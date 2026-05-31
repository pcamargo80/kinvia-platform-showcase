# Infrastructure

## Platform Overview

KINVIA runs on a self-hosted Fedora Server environment using Docker and Docker Compose.

## Edge Architecture

Internet
→ Cloudflare DNS
→ Cloudflare Proxy
→ Cloudflare Tunnel
→ Traefik
→ Authelia (when required)
→ Docker Services

## Active Components

- Cloudflare Tunnel
- Traefik
- Authelia
- Grafana
- Prometheus
- Loki
- Uptime Kuma
- n8n
- Node Exporter
- cAdvisor
- Promtail
- kinvia-web

## Internal Services

- PostgreSQL
- Redis

These services remain accessible only through the internal Docker network.

## Future Work

- GitHub Actions
- Automated deployment pipeline
- Secret management strategy
- SaaS application layer
