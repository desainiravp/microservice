# My Microservice

A Node.js microservice application with Docker and Kubernetes deployment configurations.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Local Development](#local-development)
- [Docker Deployment](#docker-deployment)
- [Kubernetes Deployment](#kubernetes-deployment)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)

## Overview

This is a simple Node.js/Express.js microservice that provides a RESTful API for managing users.

## Prerequisites

- Node.js 18+
- Docker
- Kubernetes (for K8s deployment)
- kubectl (for K8s deployment)

## Local Development

```
bash
# Install dependencies
npm install

# Start the server
npm start

# Server will run on http://localhost:3000
```

## Docker Deployment

### Build Docker Image

```
bash
docker build -t my-microservice:latest .
```

### Run with Docker Compose

```
bash
docker-compose up -d
```

### Access the Service

- API: http://localhost:3000/api
- Health: http://localhost:3000/health

## Kubernetes Deployment

### Apply Kubernetes Configurations

```
bash
# Apply deployment
kubectl apply -f k8s/deployment.yaml

# Apply service
kubectl apply -f k8s/service.yaml

# Apply ingress (optional)
kubectl apply -f k8s/ingress.yaml

# Apply configmap
kubectl apply -f k8s/configmap.yaml

# Apply HPA (optional)
kubectl apply -f k8s/hpa.yaml

# Or apply all at once
kubectl apply -f k8s/
```

### Check Deployment Status

```
bash
# Check pods
kubectl get pods -l app=my-microservice

# Check service
kubectl get svc my-microservice

# Check deployment
kubectl get deployment my-microservice

# View logs
kubectl logs -l app=my-microservice
```

### Scale Deployment

```
bash
kubectl scale deployment my-microservice --replicas=5
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /health | Health check endpoint |
| GET | /api | API information |
| GET | /api/users | Get all users |
| GET | /api/users/:id | Get user by ID |
| POST | /api/users | Create new user |

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| PORT | 3000 | Server port |
| NODE_ENV | production | Node environment |

## Example Requests

### Get All Users

```
bash
curl http://localhost:3000/api/users
```

### Create User

```
bash
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name": "John Doe", "email": "john@example.com"}'
```

## License

MIT
