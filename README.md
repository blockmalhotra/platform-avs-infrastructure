# platform-avs-infrastructure

🚧 Status: In Progress

This repository is currently under active development.
It represents a reference implementation and learning project.
Features and architecture may change before stable release.


## Features

- AVS operator reference on k8s for EigenLayer style workloads
- Docker compose with avs-operator + prom/grafana
- k8s deployment manifests
- Monitoring stack integration

## Architecture

```mermaid
graph TD
    O[Operator] --> K[K8s]
    K --> P[Prom]
    K --> G[Grafana]
```

### Component Breakdown

- **Ingress**: k8s Service port 8080 for operator; extend with ingress controller
- **Service**: avs-deployment k8s service + internal discovery
- **Storage**: Ephemeral or pvc in prod; config via k8s
- **Monitoring**: Prometheus + Grafana for operator health and AVS metrics
- **Deployment flow**: docker compose for local; kubectl apply -f k8s/ for cluster; integrate with validator ops

## Quick Start

```bash
git clone https://github.com/blockmalhotra/platform-avs-infrastructure
cd platform-avs-infrastructure
docker compose up
```

## Roadmap

### v0.1
- Initial release

### v0.2
- Feature expansion

### v0.3
- Production hardening

### v1.0
- Stable release

## Contributing

See CONTRIBUTING.md

## License

MIT License - see LICENSE file.

## Problem
Blockchain infrastructure requires production patterns for deployment, monitoring, routing and secrets.

## Components
- Docker compose for local demo
- Kubernetes manifests (StatefulSet, Service, ConfigMap, Secret)
- Observability (Prometheus, Grafana, Loki, Tempo)
- GitOps ready

## Monitoring
Prometheus metrics, Grafana dashboards, logs and traces via Loki/Tempo.

## Security
No real credentials. Secrets use CHANGEME or valueFrom. RBAC, no keys in images.

## CI/CD
.github/workflows/ci.yml: validate (compose), build (docker).

## Troubleshooting
See docs/troubleshooting.md
