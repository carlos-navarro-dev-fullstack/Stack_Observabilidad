# Observability Stack

Este repositorio contiene la configuración necesaria para levantar un entorno básico de observabilidad utilizando herramientas open source. El objetivo es centralizar métricas y logs de aplicaciones ejecutadas en contenedores Docker.

## Tecnologías

* Grafana
* Prometheus
* Loki
* Promtail
* Docker & Docker Compose

## Arquitectura

```text
                  +----------------+
                  |  Spring Boot   |
                  +-------+--------+
                          |
          +---------------+---------------+
          |                               |
          v                               v
    Prometheus                      Promtail
          |                               |
          v                               v
      Grafana  <----------------------  Loki
```

## Componentes

### Grafana

Permite visualizar métricas y consultar logs mediante dashboards y la herramienta Explore.

### Prometheus

Recolecta métricas expuestas por la aplicación a través de Spring Boot Actuator.

### Loki

Centraliza y almacena los logs generados por la aplicación.

### Promtail

Recolecta los logs desde Docker y los envía a Loki.

## Estructura del proyecto

```text
.
├── docker-compose.yml
├── prometheus/
│   └── prometheus.yml
├── loki/
│   └── loki-config.yml
└── promtail/
    └── promtail-config.yml
```

## Requisitos

* Docker
* Docker Compose

## Ejecución

Levantar todos los servicios:

```bash
docker compose up -d
```

Detener los servicios:

```bash
docker compose down
```

## Acceso a los servicios

| Servicio   | URL                   |
| ---------- | --------------------- |
| Grafana    | http://localhost:3000 |
| Prometheus | http://localhost:9090 |
| Loki       | http://localhost:3100 |

## Objetivo

Este proyecto fue desarrollado con fines de aprendizaje para comprender el funcionamiento de un stack de observabilidad moderno, integrando métricas y logs en un entorno unificado mediante Grafana, Prometheus, Loki y Promtail.
