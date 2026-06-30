# Assignment Report - CI/CD, Docker, Kubernetes & Monitoring

## First Page Mandatory Links

| Sl. No. | Submission Item | Link / Screenshot Reference |
| --- | --- | --- |
| 1 | GitHub Repository Link | `https://github.com/<username>/RegisterNumber-DevOps-Project` |
| 2 | Jenkins Build URL | Add Jenkins URL, or write `Local Jenkins - screenshots attached` |
| 3 | Docker Hub Repository Link | Optional: add Docker Hub link if pushed |
| 4 | Application URL | `http://localhost:8081` for Docker or `http://127.0.0.1:8080/index.html` for local server |
| 5 | Grafana Dashboard Screenshot | Insert screenshot page number |
| 6 | Nagios Monitoring Screenshot | Insert screenshot page number |
| 7 | Graphite Metrics Screenshot | Insert screenshot page number |

## Project Details

**Project:** ABC Technologies Corporate Website

**Student:** `<Your Name> (<Your Email>) <Register Number>`

**Use Case 1:** Corporate Company Website Deployment

ABC Technologies has designed a new corporate website consisting of HTML, CSS, JavaScript, and image files. The website contains multiple pages including Home, About Us, Services, Careers, Contact Us, and Gallery. The organization wants automatic deployment whenever developers update the website content.

## Objectives

- Automate builds using Jenkins.
- Validate the project using Maven.
- Containerize the website using Docker.
- Deploy the container on Kubernetes using Minikube or Docker Desktop Kubernetes.
- Make the website accessible through a browser.
- Monitor website availability using Nagios.
- Collect application/system metrics using Graphite.
- Visualize metrics using Grafana dashboards.

## Work Completed

- Created a multi-page corporate website using HTML, CSS, JavaScript, and images.
- Created a `Dockerfile` to host the static website using Nginx.
- Created a `pom.xml` file for Maven validation.
- Created a `Jenkinsfile` for automated CI/CD pipeline execution.
- Built the Docker image for the website.
- Ran the Docker container on port `8081`.
- Created Kubernetes `deployment.yaml`, `service.yaml`, `namespace.yaml`, `configmap.yaml`, and `ingress.yaml`.
- Deployed the website on Kubernetes and verified Pods and Services.
- Created Nagios configuration for host and HTTP service monitoring.
- Defined Graphite metric paths for CPU, memory, network, HTTP availability, and uptime.
- Created a Grafana dashboard JSON for website health visualization.

## Screenshots to Insert

### 1. GitHub Repository

Repo Link:

```text
https://github.com/<username>/RegisterNumber-DevOps-Project
```

Insert screenshot of GitHub repository page.

### 2. Jenkins Dashboard

Insert screenshot of Jenkins dashboard showing the project job.

### 3. Jenkins Job Configuration

Insert screenshot showing GitHub repository URL and Jenkinsfile path.

### 4. Successful Jenkins Console Output

Insert screenshot of console output ending with:

```text
Finished: SUCCESS
```

### 5. Maven Build Success

Insert screenshot of:

```powershell
mvn clean validate
```

Expected result:

```text
BUILD SUCCESS
```

### 6. Docker Image Build

Insert screenshot of:

```powershell
docker build -t abc-technologies-website:latest .
```

### 7. Docker Container Running

Insert screenshot of:

```powershell
docker ps
```

Show container name:

```text
abc-website
```

### 8. Application Running in Browser

Insert browser screenshot of:

```text
http://localhost:8081
```

### 9. Kubernetes Pods

Insert screenshot of:

```powershell
kubectl get pods -n abc-technologies
```

Pods should show `Running`.

### 10. Kubernetes Services

Insert screenshot of:

```powershell
kubectl get svc -n abc-technologies
```

Service should show port `30080`.

### 11. Application Running from Kubernetes

Insert screenshot of:

```text
http://localhost:30080
```

or the Minikube service URL.

### 12. Nagios Host Status

Insert screenshot showing:

```text
Host: abc-website
Status: UP
```

### 13. Nagios HTTP Service Status

Insert screenshot showing:

```text
HTTP Service: OK
```

### 14. Graphite Metrics

Insert screenshot showing metrics under:

```text
abc.website.*
```

### 15. Grafana Dashboard

Insert screenshot showing:

- CPU Usage
- Memory Usage
- Network Usage
- HTTP Availability
- Uptime

## Conclusion

The complete DevOps workflow was successfully implemented for the ABC Technologies corporate website. The website was validated using Maven, containerized using Docker, automatically built and deployed using Jenkins, deployed on Kubernetes, monitored using Nagios, and metrics were visualized using Graphite and Grafana.

