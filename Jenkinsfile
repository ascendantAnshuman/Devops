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
                sh 'mvn clean validate'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t ${IMAGE_NAME}:latest .'
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                docker rm -f ${CONTAINER_NAME} || true
                docker run -d --name ${CONTAINER_NAME} -p ${HOST_PORT}:80 ${IMAGE_NAME}:latest
                '''
            }
        }

        stage('Application Health Check') {
            steps {
                sh 'sleep 5'
                sh 'curl http://localhost:${HOST_PORT}/health.html'
            }
        }

        stage('Kubernetes Deploy') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }

    post {
        success {
            echo 'ABC Technologies website deployed successfully.'
        }

        failure {
            echo 'Build failed.'
        }
    }
}