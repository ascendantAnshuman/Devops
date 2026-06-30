# ABC Technologies Corporate Website DevOps Deployment

This project implements the requested DevOps workflow for a static corporate website.

## What Is Included

- Multi-page website: Home, About Us, Services, Careers, Contact Us, Gallery
- Maven validation build
- Jenkins pipeline
- GitHub Actions workflow for automated Docker build and Kubernetes deployment
- Dockerized Nginx hosting
- Kubernetes Deployment, Service, Ingress, and ConfigMap
- Nagios host and HTTP service checks
- Graphite metric path plan
- Grafana dashboard for CPU, memory, network, HTTP availability, and uptime

## Repository Structure

```text
corporate-website-devops/
  website/                 Static website files
  Jenkinsfile              Jenkins automation pipeline
  pom.xml                  Maven validation build
  docker/                  Nginx runtime configuration
  k8s/                     Kubernetes manifests
  monitoring/
    nagios/                Nagios host and HTTP service checks
    graphite/              Graphite metric namespace notes
    grafana/               Grafana dashboard JSON
  .github/workflows/       Portable workflow copy if this folder is used as repo root
  ../.github/workflows/    Active workflow when this workspace is pushed as one repo
```

## Local Docker Run

```bash
docker build -t abc-technologies-website:latest .
docker run -d --name abc-website -p 8080:80 abc-technologies-website:latest
```

Open `http://localhost:8080`.

## Kubernetes Deployment

```bash
kubectl apply -f k8s/
kubectl get pods -n abc-technologies
kubectl get svc -n abc-technologies
```

If Ingress is configured, browse to `http://abc-tech.local`. For local testing, add this host entry:

```text
127.0.0.1 abc-tech.local
```

## Automated Deployment

The repository-level workflow at `../.github/workflows/corporate-website-deploy.yml` runs on pushes to `main`.

Required GitHub secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`
- `KUBE_CONFIG`, base64 encoded kubeconfig

On every update, GitHub Actions:

1. Checks out source code.
2. Builds the Docker image.
3. Pushes the image to Docker Hub.
4. Applies Kubernetes manifests.
5. Waits for the rolling deployment to complete.

## Monitoring Verification

Expected final checks:

- Docker container is running.
- Kubernetes Pods and Services are running.
- Website opens in a browser.
- Nagios shows host `UP`.
- Nagios shows HTTP service `OK`.
- Graphite receives metrics under `abc.website.*`.
- Grafana dashboard displays CPU, memory, network usage, HTTP availability, and uptime.
