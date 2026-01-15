# Jenkins CI/CD Pipeline for Docker Image Build and Push

This repository demonstrates a fully automated **CI/CD pipeline** using **Jenkins** to build Docker images and push them to a Docker registry. The pipeline is triggered automatically via a **GitHub webhook** whenever code is pushed to the repository.

## Features

- Automated Docker image build and push using Jenkins.
- CI/CD pipeline defined in a `Jenkinsfile`.
- Webhook integration with GitHub for automatic pipeline triggering.
- Secure handling of Docker registry credentials via Jenkins Credentials.
- Suitable for containerized applications and microservices.

## Prerequisites

Before using this pipeline, ensure the following are installed and configured:

- **Jenkins** (running in a container or host machine)
- **Docker** installed on the Jenkins host
- **Docker Hub account** (or any container registry)
- **GitHub repository** containing your application code

## Pipeline Overview

The Jenkins pipeline performs the following steps:

1. **Checkout**: Pulls the latest code from the GitHub repository.
2. **Install Dependencies**: Installs required packages for the application (if applicable).
3. **Docker Build**: Builds a Docker image with the latest application code.
4. **Docker Push**: Pushes the Docker image to the configured Docker registry.
5. **Automated Trigger**: The pipeline is automatically triggered via a GitHub webhook whenever code is pushed to the repository.

## Setup Instructions

### Jenkins Configuration

1. Install the following Jenkins plugins:
   - **Docker Plugin**
   - **Pipeline Plugin**
   - **GitHub Integration Plugin**
2. Add Docker registry credentials in **Jenkins Credentials**.
3. Create a new **Pipeline job** in Jenkins.
4. Configure the job to use your repository and `Jenkinsfile`.

### Webhook Setup in GitHub

1. Go to your repository **Settings → Webhooks → Add webhook**.
2. Enter your Jenkins webhook URL:  
http://<JENKINS_PUBLIC_URL>/github-webhook/
3. Select **application/json** as the content type.
4. Choose **Just the push event**.
5. Save the webhook.
