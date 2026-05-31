# KINVIA Control Flows

KINVIA Control is the business application layer of the KINVIA ecosystem. It connects the public product presence, administrative interface, business modules, backend services, and infrastructure platform.

---

## 1. Functional Flow

```mermaid
flowchart LR
    A[Public Landing\nkinvia.dev] --> B[Authentication]
    B --> C[KINVIA Control\nAdmin Dashboard]
    C --> D[Users and Roles]
    C --> E[Clients]
    C --> F[Products]
    C --> G[Sales]
    C --> H[Requirements]
    C --> I[Reports]
```

Purpose:

- Show that KINVIA Control is more than a landing page.
- Present it as an internal business platform.
- Highlight admin, CRM, catalog, sales, and workflow modules.

---

## 2. SaaS Architecture Flow

```mermaid
flowchart LR
    U[User / Browser] --> CF[Cloudflare\nDNS + Proxy]
    CF --> T[Cloudflare Tunnel]
    T --> R[Traefik\nReverse Proxy]
    R --> A[Authelia\nForward Auth]
    A --> UI[KINVIA Control\nAdmin UI]
    UI --> API[Kinvia API\nFastify + TypeScript]
    API --> PG[(PostgreSQL\nInternal Only)]
    API --> RD[(Redis\nInternal Only)]
    API --> OBS[Observability\nGrafana / Prometheus / Loki]
```

Purpose:

- Document the future SaaS path.
- Keep databases private inside the Docker network.
- Show Cloudflare, Traefik, and Authelia as the public edge and access layer.

---

## 3. Business Process Flow

```mermaid
flowchart LR
    N[Business Need] --> RQ[Requirement]
    RQ --> AN[Analysis\nPriority / Scope]
    AN --> CL[Client Record]
    AN --> PR[Product / Service]
    CL --> SL[Sale / Transaction]
    PR --> SL
    SL --> ST[Status Tracking]
    ST --> RP[Operational Report]
```

Purpose:

- Explain the business workflow behind the UI.
- Position KINVIA Control as a line-of-business system.
- Demonstrate operational thinking beyond simple CRUD screens.

---

## 4. Portfolio Narrative Flow

```mermaid
flowchart LR
    P[GitHub Profile] --> S[KINVIA Platform Showcase]
    S --> L[kinvia.dev\nPublic Landing]
    S --> C[KINVIA Control\nBusiness Platform]
    S --> I[Homelab Infrastructure\nCloudflare + Traefik + Docker]
    I --> O[Observability\nGrafana + Prometheus + Loki]
    S --> M[Mobile Suite\nStudent / Home / Finance]
```

Purpose:

- Guide recruiters or clients through the story.
- Connect GitHub, landing page, control platform, infrastructure, observability, and mobile apps.
- Present the ecosystem as a complete platform instead of isolated repositories.

---

## Recommended Showcase Screenshots

Use screenshots from the video in this order:

1. KINVIA Control dashboard
2. Users / roles administration
3. Clients module
4. Products module
5. Sales module
6. Requirements or workflow module
7. Public landing page

Recommended naming:

```text
screenshots/control-dashboard.png
screenshots/control-users.png
screenshots/control-clients.png
screenshots/control-products.png
screenshots/control-sales.png
screenshots/control-requirements.png
screenshots/landing-page.png
```

---

## Positioning

KINVIA Control should be presented as the business application layer of KINVIA:

- Administrative dashboard
- Business modules
- Operational workflows
- Future SaaS backend integration
- Infrastructure-backed deployment model

This makes the portfolio stronger because it shows not only infrastructure, but also a real business application running on top of that infrastructure.
