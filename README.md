# Python Django 3-Tier Student Management System

A containerized 3-tier Student Management System built with Django REST Framework, PostgreSQL, Nginx, Docker, and Kubernetes. The project is structured to demonstrate application containerization and DevOps-oriented CI/CD workflows.

## Project Overview

This project follows a 3-tier architecture:

- **Frontend:** HTML, CSS, JavaScript served through Nginx
- **Backend:** Django REST Framework API
- **Database:** PostgreSQL

The application is containerized using Docker and includes Kubernetes manifests for deployment. A Jenkins pipeline is also included to demonstrate a CI/CD workflow.

## Architecture

```text
                    User
                      |
                      v
              +---------------+
              |    Nginx      |
              |   Frontend    |
              +---------------+
                      |
                      | /api/
                      v
              +---------------+
              |    Django     |
              |   REST API    |
              +---------------+
                      |
                      v
              +---------------+
              |  PostgreSQL   |
              |    Database   |
              +---------------+
---
## Technology Stack

### Application

* Python
* Django
* Django REST Framework
* PostgreSQL
* HTML
* CSS
* JavaScript

### DevOps

* Git
* GitHub
* Jenkins
* Docker
* Docker Hub
* Kubernetes
* Nginx

## Project Structure

```text
python-django-3tier-devops/
│
├── frontend/
│   ├── Dockerfile
│   ├── nginx.conf
│   ├── index.html
│   ├── app.js
│   └── style.css
│
├── backend/
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── manage.py
│   │
│   ├── config/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── wsgi.py
│   │   └── ...
│   │
│   └── students/
│       ├── models.py
│       ├── views.py
│       ├── urls.py
│       └── ...
│
├── k8s/
│   ├── namespace.yaml
│   ├── postgres-secret.yaml
│   ├── postgres.yaml
│   ├── backend.yaml
│   └── frontend.yaml
│
├── docker-compose.yml
├── Jenkinsfile
├── .gitignore
└── README.md
```

## Application Features

The Student Management System provides basic CRUD functionality for student records.

### Student Operations

* Add a student
* View students
* Update student details
* Delete a student

### Student Fields

* Name
* Email
* Course
* Age

## Docker Configuration

Separate Dockerfiles are used for the frontend and backend.

### Frontend

The frontend uses Nginx to serve the static files and reverse-proxy API requests to the Django backend.

```text
frontend/Dockerfile
```

### Backend

The backend uses Python and Gunicorn to run the Django REST API.

```text
backend/Dockerfile
```

## Docker Compose

A `docker-compose.yml` file is included to define the application services:

```text
Frontend
   |
   v
Backend
   |
   v
PostgreSQL
```

The services communicate with each other through the Docker network created by Docker Compose.

## Kubernetes

The project includes Kubernetes manifests for running the application components.

### Kubernetes Components

```text
k8s/
├── namespace.yaml
├── postgres-secret.yaml
├── postgres.yaml
├── backend.yaml
└── frontend.yaml
```

The manifests define:

* Namespace
* PostgreSQL deployment and service
* Backend deployment and service
* Frontend deployment and service
* Database configuration

## CI/CD Workflow

The project includes a Jenkins pipeline designed around the following workflow:

```text
Developer
    |
    v
  GitHub
    |
    v
  Jenkins
    |
    +----> Code Analysis
    |
    +----> Docker Build
    |
    +----> Docker Images
    |
    v
 Docker Hub
    |
    v
 Kubernetes
```

### Pipeline Stages

1. Checkout source code from GitHub
2. Perform code analysis
3. Build frontend Docker image
4. Build backend Docker image
5. Push images to Docker Hub
6. Deploy using Kubernetes manifests

## Docker Images

The project uses separate images for the application layers:

```text
Frontend Image
      |
      v
Nginx

Backend Image
      |
      v
Django + Gunicorn
```

The Docker image names can be configured in the Jenkins pipeline according to the Docker Hub username.

## Configuration

Before using the project, update the placeholder values used for environment-specific configuration.

Examples:

```text
YOUR_DOCKERHUB_USERNAME
CHANGE_ME
```

Do not store real passwords, API keys, Docker Hub credentials, or other secrets directly in the Git repository.

## Learning Objectives

This project demonstrates practical understanding of:

* 3-tier application architecture
* Django REST API development
* PostgreSQL integration
* Docker containerization
* Docker networking
* Nginx reverse proxy
* Kubernetes deployments and services
* Jenkins CI/CD pipeline structure
* Docker image management
* Git and GitHub workflow

## DevOps Workflow

The overall workflow of the project is:

```text
Code
  ↓
GitHub
  ↓
Jenkins
  ↓
Code Analysis
  ↓
Docker Build
  ↓
Docker Hub
  ↓
Kubernetes
  ↓
Application
```
