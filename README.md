# K8s App

This repository contains Kubernetes manifests for a simple application consisting of a frontend, backend, and database, developed using a three-tier architecture:

- **Backend**: Written in Go, utilizing the 'chi' package for routing.  
  GitHub link: [github.com/AbdoAnss/simple-go-backend](https://github.com/AbdoAnss/simple-go-backend)
  
- **Frontend**: Built with Deno, React, and Vite, styled using Tailwind CSS.  
  GitHub link: [github.com/AbdoAnss/simple-react-frontend](https://github.com/AbdoAnss/simple-react-frontend)
  
- **Database**: MySQL version 8.0.

## Directory Structure

1. **database.yaml** - Contains MySQL StatefulSet, Service, and Secret.
2. **backend.yaml** - Go backend with health probes and resource limits.
3. **frontend.yaml** - React frontend with health probes and resource limits.
4. **ingress.yaml** - Ingress configuration for routing traffic to services.
5. **pdb.yaml** - Pod Disruption Budget for both frontend and backend.
6. **quota.yaml** - Resource Quotas for the exam namespace.
7. **rbac.yaml** - Role-Based Access Control configuration.

## Usage

1. Start Minikube and get its IP address:
   ```bash
   minikube start
   minikube ip
   ```

2. Add the IP address to your hosts file:
   - On **Windows**: `C:\Windows\System32\drivers\etc\hosts`
   - On **macOS/Linux**: `/etc/hosts`

   Example entry:
   ```
   <minikube-ip> app.local
   ```

3. Create a new namespace (recommended):
   ```bash
   kubectl create namespace my-app
   ```

4. Apply the manifests to your Kubernetes cluster:
   ```bash
   kubectl apply -f . -n my-app
   ```

5. Access the application via the ingress endpoint:
   - Frontend: `http://app.local`
   - Backend: `http://app.local/api/students`

## Prerequisites

- Kubernetes cluster (Minikube recommended)
- `kubectl` command-line tool installed

