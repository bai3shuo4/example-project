# Kubernetes Example Project

This is a sample project that demonstrates how to deploy an Nginx application using Kubernetes. The project includes complete Kubernetes resource configurations for deploying and managing a simple web application.

## Project Structure

- `deployment.yaml`: Defines the application deployment configuration
- `service.yaml`: Defines the Kubernetes Service
- `ingress.yaml`: Configures Ingress rules
- `config.yaml`: Application configuration
- `secret.yaml`: Sensitive information configuration

## Deployment Instructions

### Prerequisites

- Kubernetes cluster
- kubectl command-line tool
- Ingress Controller installed in the cluster

### Deployment Steps

1. Create configuration and secrets:
```bash
kubectl apply -f config.yaml
kubectl apply -f secret.yaml
```

2. Deploy the application:
```bash
kubectl apply -f deployment.yaml
```

3. Create the service:
```bash
kubectl apply -f service.yaml
```

4. Configure Ingress:
```bash
kubectl apply -f ingress.yaml
```

## Configuration Details

- Application uses the latest version of Nginx
- Default deployment with 2 replicas
- Service type is ClusterIP
- Ingress configured for example.local domain
- Application configuration injected via ConfigMap and Secret

## Accessing the Application

Configure your local hosts file by adding the following entry:
```
clusterIP example.local
```

Then access the application through your browser at: http://example.local

## Important Notes

- Ensure the Kubernetes cluster is running properly
- Verify that the Ingress Controller is correctly configured
- Modify configuration parameters according to your needs 