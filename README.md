# NodeKube CI/CD Pipeline

A CI/CD pipeline implementation for a Node.js application using GitHub Actions, Docker, and Kubernetes (Minikube). This project demonstrates automated testing, Docker image building, and Kubernetes deployment workflows.

## Features

- Automated testing on pull requests
- Docker image building and publishing
- Kubernetes deployment using Minikube
- Deployment status notifications
- GitHub Actions workflow integration

## Prerequisites

- Node.js (v14 or higher)
- Docker
- Minikube
- kubectl
- GitHub account
- Docker Hub account
- ngrok (for local Kubernetes access)

## Setup Instructions

### 1. Local Development Setup

```bash
# Clone the repository
git clone https://github.com/Yasin-Siddiquee/NodeKube-CI-CD.git
cd NodeKube-CI-CD

# Install dependencies
npm install

# Run tests locally
npm test
```

### 2. Minikube Setup

```bash
# Start Minikube
minikube start --driver=docker

# Verify Minikube status
minikube status
```

### 3. Docker Setup

```bash
# Build Docker image
docker build -t your-dockerhub-username/nodekube-ci-cd .

# Run container locally
docker run -p 3000:3000 your-dockerhub-username/nodekube-ci-cd
```

### 4. GitHub Actions Configuration
1. Add the following secrets to your GitHub repository:
   - DOCKER_USERNAME: Your Docker Hub username
   - DOCKER_PASSWORD: Your Docker Hub access token
   - KUBECONFIG: Your base64 encoded kubeconfig file
2. The workflow will automatically:
   - Run tests on pull requests
   - Build and push Docker images
   - Deploy to Kubernetes
   - Send deployment notifications

## Project Structure

```markdown
.
├── .github/
│   └── workflows/
│       └── ci-cd-pipeline.yml
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── Dockerfile
├── package.json
└── README.md
```

## Workflow

1. Create a pull request to trigger the CI/CD pipeline
2. GitHub Actions will:
   - Run automated tests
   - Build Docker image
   - Push to Docker Hub
   - Deploy to Kubernetes
   - Send notification of deployment status
  
## Deployment

The application is deployed to a Kubernetes cluster using the configurations in the k8s/ directory:
- deployment.yaml: Defines the Kubernetes deployment
- service.yaml: Defines the Kubernetes service
