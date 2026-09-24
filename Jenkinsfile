pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'YOUR_DOCKERHUB_USERNAME'
        FRONTEND_IMAGE = "${DOCKERHUB_USER}/python-django-frontend"
        BACKEND_IMAGE  = "${DOCKERHUB_USER}/python-django-backend"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Code Quality') {
            steps {
                echo 'Run SonarQube analysis here.'
            }
        }

        stage('Build Backend Image') {
            steps {
                sh 'docker build -t ${BACKEND_IMAGE}:${IMAGE_TAG} ./backend'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t ${FRONTEND_IMAGE}:${IMAGE_TAG} ./frontend'
            }
        }

        stage('Push Images') {
            steps {
                echo 'Authenticate with Docker Hub using Jenkins credentials before pushing.'
                sh 'docker push ${BACKEND_IMAGE}:${IMAGE_TAG}'
                sh 'docker push ${FRONTEND_IMAGE}:${IMAGE_TAG}'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy Kubernetes manifests and update image tags here.'
            }
        }
    }
}
