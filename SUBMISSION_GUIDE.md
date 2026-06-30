# Full Marks Submission Guide

Use this guide to complete the required proof for the DevOps project.

## First Page Links

Add these items on the first page of your report:

| Item | What to Add |
| --- | --- |
| GitHub Repository Link | `https://github.com/<your-username>/RegisterNumber-DevOps-Project` |
| Jenkins Build URL | Jenkins job URL, or screenshots if Jenkins is local |
| Docker Hub Repository Link | Optional Docker Hub repository URL |
| Application URL | `http://localhost:8080/index.html` for Python server or `http://localhost:8081` for Docker |
| Grafana Dashboard Screenshot | Screenshot of CPU, memory, network, HTTP availability, uptime |
| Nagios Monitoring Screenshot | Screenshot showing Host UP and HTTP Service OK |
| Graphite Metrics Screenshot | Screenshot showing received `abc.website.*` metrics |

## Screenshot Checklist

Take screenshots for each step:

1. Project folder opened in VS Code.
2. GitHub repository page.
3. Git push command or uploaded repository files.
4. Jenkins dashboard.
5. Jenkins job configuration.
6. Jenkins console output.
7. Jenkins successful build.
8. Maven build success.
9. Docker image created.
10. Docker container running.
11. Website opened in browser.
12. Kubernetes pods running.
13. Kubernetes services running.
14. Nagios Host UP and HTTP Service OK.
15. Graphite metrics screen.
16. Grafana dashboard screen.

## Important Commands

### Run Website Locally

```powershell
cd "C:\Users\HP\OneDrive\Desktop\final yera\corporate-website-devops\website"
python -m http.server 8080 --bind 127.0.0.1
```

Open:

```text
http://127.0.0.1:8080/index.html
```

### Maven Build

Install Maven first if `mvn` is not recognized.

```powershell
cd "C:\Users\HP\OneDrive\Desktop\final yera\corporate-website-devops"
mvn clean validate
```

### Docker Build and Run

Start Docker Desktop first.

```powershell
cd "C:\Users\HP\OneDrive\Desktop\final yera\corporate-website-devops"
docker build -t abc-technologies-website:latest .
docker run -d --name abc-website -p 8081:80 abc-technologies-website:latest
docker ps
```

Open:

```text
http://localhost:8081
```

### Kubernetes Deploy

Start Minikube or Docker Desktop Kubernetes first.

```powershell
cd "C:\Users\HP\OneDrive\Desktop\final yera\corporate-website-devops"
kubectl apply -f k8s/
kubectl get pods -n abc-technologies
kubectl get svc -n abc-technologies
```

### Zip Naming

Replace placeholders with your real register number and name:

```text
RegisterNumber_Name_DevOps_Project.zip
RegisterNumber_Name_DevOps_Report.pdf
RegisterNumber-DevOps-Project
```

