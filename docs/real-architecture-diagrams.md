# Real Architecture Diagrams

These diagrams document the current KINVIA platform architecture based on the homelab, API, landing and platform showcase repositories.

---

## 1. Real Platform Architecture

```mermaid
flowchart LR
    Internet[Internet] --> CF[Cloudflare\nDNS + Proxy + TLS]
    CF --> Tunnel[Cloudflare Tunnel\ncloudflared]
    Tunnel --> Traefik[Traefik\nReverse Proxy]

    Traefik -->|public| Web[kinvia-web\nNginx + Astro dist]
    Traefik -->|api.kinvia.dev| API[kinvia-api\nFastify + TypeScript]
    Traefik -->|protected routes| Authelia[Authelia\nSSO / Forward Auth]

    Authelia --> Grafana[Grafana]
    Authelia --> Prometheus[Prometheus]
    Authelia --> Loki[Loki]
    Authelia --> Uptime[Uptime Kuma]

    API --> Postgres[(PostgreSQL\nInternal network)]
    API -.-> Redis[(Redis\nInternal network)]
    n8n[n8n\nAutomation] -. workflows .-> API
```

---

## 2. External Exposure Matrix

```mermaid
flowchart TB
    subgraph Public[Public]
      Landing[kinvia.dev\nLanding]
      WWW[www.kinvia.dev\nLanding]
      Auth[auth.kinvia.dev\nAuthelia login]
      Api[api.kinvia.dev\nKinvia API]
    end

    subgraph Protected[Authelia protected]
      Grafana[grafana.kinvia.dev]
      Prometheus[prometheus.kinvia.dev]
      Loki[loki.kinvia.dev]
      Uptime[uptime.kinvia.dev]
    end

    subgraph Internal[Internal only]
      NodeExporter[Node Exporter]
      Cadvisor[cAdvisor]
      Promtail[Promtail]
      Data[PostgreSQL / Redis]
      TraefikDashboard[Traefik Dashboard]
    end
```

---

## 3. Observability Architecture

```mermaid
flowchart LR
    Host[Fedora host] --> NodeExporter[Node Exporter\nHost metrics]
    Containers[Docker containers] --> Cadvisor[cAdvisor\nContainer metrics]
    API[Kinvia API\n/metrics] --> Prometheus[Prometheus\nScraping + storage]

    NodeExporter --> Prometheus
    Cadvisor --> Prometheus
    Prometheus --> Grafana[Grafana\nDashboards]

    Containers --> Promtail[Promtail\nDocker log shipping]
    Promtail --> Loki[Loki\nLog aggregation]
    Loki --> Grafana

    Uptime[Uptime Kuma\nAvailability checks] -. status context .-> Grafana
```

---

## 4. API Runtime and Delivery Flow

```mermaid
flowchart LR
    Repo[kinvia-api repo] --> Actions[GitHub Actions\nCI/CD]
    Actions --> GHCR[GHCR image\nkinvia-api:latest]
    GHCR --> Compose[Docker Compose\nHomelab deploy]
    Compose --> Container[kinvia-api container\nNode 22 + Fastify]

    Container --> Prisma[Prisma 7]
    Prisma --> Postgres[(PostgreSQL 16)]

    Traefik[Traefik] --> APIURL[api.kinvia.dev]
    APIURL --> Container
    Container --> Swagger[Swagger\n/docs + /docs/json]
    Container --> Metrics[Prometheus metrics\n/metrics]
```

---

## 5. Landing Site Delivery Flow

```mermaid
flowchart LR
    I18N[ES/EN content\nsrc/i18n] --> Astro[Astro + TypeScript\nTailwind CSS]
    Sections[Component sections\nHero · Services · Portfolio · Contact] --> Astro
    Astro --> Build[Astro build\ndist/]
    Build --> Nginx[kinvia-web\nNginx container]
    Nginx --> Traefik[Traefik]
    Traefik --> Tunnel[Cloudflare Tunnel]
    Tunnel --> Domain[kinvia.dev\nwww.kinvia.dev]
```

---

## Notes

- Public traffic enters through Cloudflare DNS/Proxy/TLS and Cloudflare Tunnel.
- Traefik is the main reverse proxy inside the homelab.
- Authelia protects observability and internal-facing tools.
- PostgreSQL and Redis are internal services and should not be exposed directly.
- Grafana, Prometheus, Loki and Uptime Kuma make up the operational visibility layer.
- KINVIA Site is the public commercial surface.
- KINVIA API is the backend foundation for future SaaS capabilities.
