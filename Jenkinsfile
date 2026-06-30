pipeline {
    agent any

    environment {
        IMAGE_NAME = 'abc-technologies-website'
        CONTAINER_NAME = 'abc-website'
        HOST_PORT = '8081'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Maven Build') {
            steps {
                dir('corporate-website-devops') {
                    bat 'mvn clean validate'
                }
            }
        }

        stage('Docker Build') {
            steps {
                dir('corporate-website-devops') {
                    bat 'docker build -t %IMAGE_NAME%:latest .'
                }
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker rm -f %CONTAINER_NAME% || exit 0'
                bat 'docker run -d --name %CONTAINER_NAME% -p %HOST_PORT%:80 %IMAGE_NAME%:latest'
            }
        }

        stage('Application Health Check') {
            steps {
                bat 'powershell -Command "Start-Sleep -Seconds 3; Invoke-WebRequest -Uri http://localhost:%HOST_PORT%/health.html -UseBasicParsing"'
            }
        }

        stage('Kubernetes Deploy') {
            steps {
                dir('corporate-website-devops') {
                    bat 'kubectl apply -f k8s/'
                    bat 'kubectl rollout status deployment/abc-website -n abc-technologies --timeout=180s'
                }
            }
        }
    }

    post {
        success {
            echo 'ABC Technologies website build and deployment completed successfully.'
        }
        failure {
            echo 'Build failed. Check Maven, Docker, Kubernetes, and Jenkins configuration.'
        }
    }
}

