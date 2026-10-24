# Cloud & DevOps Learning Hub

A beginner-friendly Cloud/DevOps project built by two friends to learn Git, GitHub, Docker, Nginx, and AWS EC2 through a real-world website deployment.

## Project Overview

We created a custom HTML website, packaged it into a Docker image using Nginx, and ran it locally in a Docker container. Our next goal is to deploy the same website on an AWS EC2 Linux instance.

## Technology Stack

- **HTML** — Website content
- **Git** — Version control
- **GitHub** — Source code hosting and collaboration
- **Docker** — Application containerization
- **Nginx** — Web server
- **AWS EC2** — Planned cloud deployment
- **Ubuntu on WSL2** — Local development environment

## Architecture

```text
Developer
   |
   v
HTML Website (index.html)
   |
   v
Git Repository
   |
   v
GitHub Repository
   |
   v
Docker Image (cloud-pra:v1)
   |
   v
Docker Container (cloud-pra-web)
   |
   v
Nginx Web Server
   |
   v
Browser: http://localhost:8080

Planned next step:
Docker Container on AWS EC2
   |
   v
Public Browser Access over HTTP
```

## Project Files

```text
cloud-pra/
├── index.html
├── Dockerfile
└── README.md
```

## Run the Website Locally

### Prerequisites

- Git
- Docker Desktop with WSL2 integration enabled
- Ubuntu on WSL2

### 1. Clone the Repository

```bash
git clone https://github.com/MansiPandey-git/cloud-pra.git
cd cloud-pra
```

### 2. Build the Docker Image

```bash
docker build -t cloud-pra:v1 .
```

### 3. Run the Container

```bash
docker run -d --name cloud-pra-web -p 8080:80 cloud-pra:v1
```

### 4. Open the Website

Visit the following address in your browser:

http://localhost:8080

### 5. Stop the Container

```bash
docker stop cloud-pra-web
```

To start it again:

```bash
docker start cloud-pra-web
```

## Dockerfile

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

The Dockerfile uses the lightweight Nginx Alpine image, copies our HTML page into Nginx's default website directory, and documents port 80 as the container's web port.

## Git Workflow

Initialize the repository:

```bash
git init
git branch -m main
```

Stage and commit changes:

```bash
git add index.html Dockerfile README.md
git commit -m "Add project documentation"
```

Push changes to GitHub:

```bash
git push origin main
```

## Team Collaboration

We are working as a team of two.

- **Developer 1:** Website development and README documentation.
- **Developer 2:** Docker verification and deployment testing.

Both team members will practise Git and Docker commands. We will use branches and pull requests when collaborating on changes to avoid overwriting each other's work.

## Planned AWS Deployment

Our next phase is to deploy the Dockerized website on an AWS EC2 Linux instance.

Planned steps:

1. Review AWS billing, available credits, and possible charges.
2. Select a suitable small EC2 instance after checking current pricing.
3. Configure SSH access restricted to our own IP address where possible.
4. Allow inbound HTTP traffic on port 80 for website access.
5. Install Docker on the EC2 instance.
6. Clone the GitHub repository and build the Docker image.
7. Run the container with the appropriate port mapping.
8. Test the website using the EC2 public address.

AWS resources will only be created after reviewing potential costs and confirming the plan.

## Security Considerations

- Never commit passwords, personal access tokens, or private SSH keys.
- Use secure GitHub authentication.
- Restrict SSH access to trusted IP addresses.
- Review AWS costs before launching resources.
- Stop or terminate unused AWS resources and check for remaining chargeable resources.

## Learning Outcomes

Through this project, we aim to learn:

- Basic Git version control and GitHub collaboration.
- Docker image creation and container execution.
- Nginx-based website hosting.
- Port mapping and local website testing.
- Cloud deployment using AWS EC2.
- Basic cloud security, cost awareness, and cleanup.

