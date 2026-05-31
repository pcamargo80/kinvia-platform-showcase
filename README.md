# KINVIA Platform

## Overview

KINVIA Platform es una plataforma self-hosted diseñada para experimentar, validar y operar servicios modernos de infraestructura, observabilidad, automatización y aplicaciones.

El proyecto integra componentes de seguridad, monitoreo, automatización, backend y aplicaciones móviles bajo una arquitectura unificada.

## Objetivos

* Centralizar servicios internos.
* Implementar observabilidad completa.
* Validar patrones modernos de infraestructura.
* Construir aplicaciones sobre una plataforma propia.
* Mantener control total sobre datos y despliegues.

---

## Arquitectura General

Internet
↓
Cloudflare
↓
Cloudflare Tunnel
↓
Traefik
↓
Authelia
↓
Servicios Docker

Servicios principales:

* Kinvia Web
* n8n
* Grafana
* Prometheus
* Loki
* Uptime Kuma
* APIs internas

---

## Infraestructura

Sistema operativo:

* Fedora Server

Contenedorización:

* Docker
* Docker Compose

Servicios de red:

* Cloudflare Tunnel
* Traefik Reverse Proxy

Seguridad:

* Authelia Forward Authentication
* Single Sign-On (SSO)
* HTTPS end-to-end

---

## Observabilidad

La plataforma incorpora un stack completo de monitoreo y observabilidad.

### Métricas

* Prometheus
* Node Exporter
* cAdvisor

### Logs

* Loki
* Promtail

### Visualización

* Grafana

### Disponibilidad

* Uptime Kuma

Capacidades actuales:

* Métricas de host
* Métricas de contenedores
* Logs centralizados
* Dashboards operativos
* Monitoreo de disponibilidad

---

## Seguridad

La capa de acceso está protegida mediante Authelia integrado con Traefik.

Servicios protegidos:

* Grafana
* Prometheus
* Loki
* Uptime Kuma

Política actual:

* One Factor Authentication

Roadmap:

* Multi-Factor Authentication (MFA)
* Políticas avanzadas de acceso
* Gestión centralizada de identidades

---

## Aplicaciones

### Kinvia API

Backend desarrollado con:

* Node.js
* TypeScript
* Fastify
* Prisma
* PostgreSQL

Características:

* REST API
* Swagger/OpenAPI
* Métricas Prometheus
* Docker Ready

### Kinvia Student

Aplicación móvil para gestión académica.

Tecnologías:

* Flutter
* Riverpod
* Hive
* Material 3

### Kinvia Home

Aplicación móvil para gestión de compras domésticas.

Tecnologías:

* Flutter
* Riverpod
* Hive

### Kinvia Finance

Aplicación móvil para finanzas personales.

Tecnologías:

* Flutter
* Riverpod
* Hive
* Local Notifications

---

## Automatización

La plataforma incorpora n8n para automatización de procesos y orquestación de flujos.

Objetivos:

* Integraciones
* Automatización operativa
* Flujos asistidos por IA
* Procesamiento de eventos

---

## Estado Actual

Operativo.

Componentes activos:

* Infraestructura base
* Seguridad
* Observabilidad
* Landing pública
* Backend principal
* Aplicaciones móviles en desarrollo

---

## Roadmap

### Infraestructura

* GitHub Actions
* CI/CD automatizado
* Despliegues automáticos
* Gestión centralizada de secretos

### Seguridad

* MFA con Authelia
* Hardening de servicios
* Auditoría de acceso

### Plataforma

* Nuevos módulos Kinvia
* Integraciones IA
* APIs adicionales
* Automatización avanzada
