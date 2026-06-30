# Use Case 1 Implementation Report

## Requirement Mapping

| Requirement | Implementation |
| --- | --- |
| Multiple developers collaborate | Source code is stored in a Git repository and deployed from the `main` branch. |
| Every update triggers deployment | GitHub Actions workflow runs on pushes to `main`. |
| Website hosted in Docker | `Dockerfile` packages the static website with Nginx. |
| Container deployed in Kubernetes | `k8s/deployment.yaml` runs 3 replicas with rolling updates. |
| Website accessible in browser | `k8s/service.yaml` exposes NodePort `30080`; `k8s/ingress.yaml` exposes `abc-tech.local`. |
| Website availability monitored | `monitoring/nagios/abc-website.cfg` checks host availability and `/health.html`. |
| Metrics collected | Graphite metric namespace is documented in `monitoring/graphite/metrics.md`. |
| Dashboards available | Grafana dashboard JSON is provided in `monitoring/grafana/abc-website-dashboard.json`. |

## Demonstration Commands

```bash
git status
docker build -t abc-technologies-website:latest .
docker run -d --name abc-website -p 8080:80 abc-technologies-website:latest
kubectl apply -f k8s/
kubectl get pods -n abc-technologies
kubectl get svc -n abc-technologies
```

## Expected Final Output

- Git repository contains website source and DevOps configuration.
- GitHub Actions build completes successfully after required secrets are configured.
- Docker container serves the website with Nginx.
- Kubernetes Deployment runs 3 website pods.
- Kubernetes Service exposes the website on port `30080`.
- Browser access works through NodePort or Ingress.
- Nagios shows host `UP` and HTTP service `OK`.
- Graphite receives metrics under `abc.website.*`.
- Grafana dashboard displays CPU, memory, network, HTTP availability, and uptime.

