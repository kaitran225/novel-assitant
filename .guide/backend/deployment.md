# Backend Deployment & Scaling

## Deployment Options

- Local (single machine, for individuals)
- On-premises (enterprise, private cloud)
- Cloud (Docker, Kubernetes, managed DB)

## Steps

1. Build Docker images for all backend services.
2. Configure environment variables (DB, secrets, API keys).
3. Deploy with Docker Compose or Helm charts.
4. Set up HTTPS, firewalls, and monitoring.
5. Run health checks and smoke tests.

## Scaling

- Stateless API enables horizontal scaling.
- Use load balancers for high availability.
- DB can be scaled with managed Postgres/Cloud SQL for enterprise.

---

For monitoring, see `monitoring.md`.
