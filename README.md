🚀 Angular Docker Deployment on Azure
📌 Project Overview

This project is a production-ready Angular frontend application containerized using Docker and deployed to Microsoft Azure App Service (Linux).

The application is built using a multi-stage Docker build process and served through NGINX for optimized performance and proper client-side routing support.

🏗️ Architecture

Angular App
⬇
Docker Multi-Stage Build
⬇
NGINX (serving static build)
⬇
Docker Hub (image registry)
⬇
Azure App Service (Linux Container)

🐳 Docker Setup
Multi-Stage Build

Stage 1 – Build

Uses Node.js to install dependencies

Builds Angular app for production

Stage 2 – Serve

Uses lightweight NGINX image

Serves compiled files from /usr/share/nginx/html

Configured with try_files to support Angular routing

Build Image
docker build -t <dockerhub-username>/angular-app:latest .
Push Image
docker push <dockerhub-username>/angular-app:latest
☁️ Azure Deployment

The Docker image is deployed using Azure App Service (Linux) configured to run a custom container.

Key Configuration

Runtime: Linux container

Port: 80

Environment Variable:

WEBSITES_PORT=80

Application URL:

https://<app-name>.azurewebsites.net
📂 Project Structure
.
├── src/
├── dist/
├── Dockerfile
├── nginx.conf
└── package.json
🔥 Key Features

Production Angular build

Multi-stage Docker optimization

Lightweight NGINX container

Angular routing support

Cloud deployment ready

Scalable via Azure infrastructure

🧠 What I Learned

Containerizing frontend applications

Multi-stage Docker builds

NGINX configuration for SPA routing

Deploying containers to Azure App Service

Managing cloud-based container deployments

📜 License

This project is for learning and deployment practice purposes.

If you want, I can also give you:

🔹 A more “portfolio showcase” version (impress recruiters)

🔹 A super minimal clean README

🔹 Or a backend + full stack version if your Node API is included

Tell me where you’re planning to use it — job portfolio, internship, or personal learning?

make it interactive without using azure you have to use github actions ci/cd pipeline , docker ,linux

Ohhh okay 🔥 now we’re building something that actually looks like DevOps experience.

You want:

✅ Angular

✅ Docker

✅ Linux

✅ GitHub Actions CI/CD

❌ No Azure

🎯 Clean but interactive README

Love it. I’ll give you a portfolio-ready README with badges, pipeline explanation, and workflow clarity.

You can copy this directly 👇

🚀 Angular CI/CD Docker Pipeline (Linux Based)








📌 Project Overview

This project demonstrates a production-ready Angular application containerized using Docker and automatically built & deployed using a GitHub Actions CI/CD pipeline on a Linux environment.

Every push to the main branch triggers:

🔨 Angular production build

🐳 Docker image build

📦 Docker image push to Docker Hub

🚀 Automated deployment update

This project simulates a real-world DevOps workflow without using any cloud provider.

🏗️ Architecture
Developer Push → GitHub → GitHub Actions (Linux Runner)
                 ↓
          Angular Production Build
                 ↓
           Docker Image Build
                 ↓
         Push to Docker Hub
                 ↓
       Pull & Run on Linux Server
🐳 Docker Setup
Multi-Stage Dockerfile

Stage 1: Builds Angular app using Node.js

Stage 2: Serves static files using NGINX

Optimized for lightweight production deployment.

Build Image Locally
docker build -t <dockerhub-username>/angular-app:latest .
Run Container (Linux)
docker run -d -p 80:80 <dockerhub-username>/angular-app:latest
🔄 CI/CD Pipeline (GitHub Actions)

The pipeline is defined in:

.github/workflows/docker-deploy.yml
Pipeline Triggers

Push to main

Pull requests (optional)

Pipeline Steps

Checkout repository

Set up Node.js

Install dependencies

Build Angular app

Login to Docker Hub

Build Docker image

Push image to Docker Hub

🛠️ Example GitHub Actions Workflow
name: Docker CI/CD

on:
  push:
    branches: [ "main" ]

jobs:
  build-and-push:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Set up Node
      uses: actions/setup-node@v4
      with:
        node-version: 18

    - name: Install dependencies
      run: npm install

    - name: Build Angular app
      run: npm run build --configuration production

    - name: Login to Docker Hub
      uses: docker/login-action@v3
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker image
      run: docker build -t ${{ secrets.DOCKER_USERNAME }}/angular-app:latest .

    - name: Push Docker image
      run: docker push ${{ secrets.DOCKER_USERNAME }}/angular-app:latest
🔐 Required GitHub Secrets

Inside repository → Settings → Secrets:

DOCKER_USERNAME

DOCKER_PASSWORD

🐧 Linux Deployment

On your Linux server:

docker pull <dockerhub-username>/angular-app:latest
docker run -d -p 80:80 <dockerhub-username>/angular-app:latest

You can also automate this using a self-hosted runner for full CD.

📂 Project Structure
.
├── src/
├── Dockerfile
├── nginx.conf
├── .github/
│   └── workflows/
│       └── docker-deploy.yml
└── package.json
🔥 Key Features

Production-ready Angular build

Multi-stage Docker optimization

NGINX SPA routing configuration

Automated CI/CD using GitHub Actions

Linux container deployment

Docker Hub image management

📈 DevOps Concepts Demonstrated

CI/CD pipeline automation

Secret management

Containerization

Linux-based deployment

Version-controlled infrastructure

🧠 Learning Outcome

This project demonstrates practical knowledge of:

Modern frontend deployment workflows

Docker container lifecycle

GitHub Actions automation

Linux-based container hosting

End-to-end CI/CD pipeline design
