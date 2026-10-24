# Cloud & DevOps Learning Hub

A hands-on Cloud and DevOps project demonstrating Git, GitHub, Docker, Nginx, and deployment of a containerized website on an AWS EC2 instance.

## Project Overview

The goal of this project is to build a simple website, package it into a Docker image, and deploy it on an AWS EC2 virtual server so that it can be accessed through a web browser.

## Technologies Used

- **Git** – Version control
- **GitHub** – Source code hosting
- **Docker** – Containerization
- **Dockerfile** – Instructions to build the Docker image
- **Nginx** – Web server
- **AWS EC2** – Cloud virtual machine
- **Ubuntu Linux** – Operating system
- **Security Groups** – Network access control

## Project Architecture

Developer → Git → GitHub → AWS EC2 (Ubuntu) → Docker Container → Nginx Web Server → Website

## Project 1: Build a Website Using Docker

### 1. Create the Website

Created an `index.html` file displaying the Cloud & DevOps Learning Hub webpage.

### 2. Create the Dockerfile

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

**Explanation:**
- `FROM nginx:alpine` – Uses the lightweight Nginx image.
- `COPY` – Copies the website into Nginx's web directory.
- `EXPOSE 80` – Documents the port used by the web server.

### 3. Build the Docker Image

```bash
docker build -t cloud-pra:v1 .
```

### 4. Run the Container Locally

```bash
docker run -d --name cloud-pra-web -p 8080:80 cloud-pra:v1
```

Open `http://localhost:8080` to verify the website.

## Project 2: Install Docker on AWS EC2

### 1. Launch an EC2 Instance

- Launched an Ubuntu EC2 instance on AWS.
- Configured a security group to allow SSH access from my IP address.
- Allowed inbound HTTP traffic on port 80 to access the website.

### 2. Connect to EC2 Using SSH

```bash
chmod 400 cloud-pra-key.pem
ssh -i cloud-pra-key.pem ubuntu@<EC2-PUBLIC-IP>
```

Replace `<EC2-PUBLIC-IP>` with your instance's public IP address.

### 3. Update Ubuntu Packages

```bash
sudo apt update
```

### 4. Install Docker

```bash
sudo apt install -y docker.io
```

### 5. Start Docker

```bash
sudo systemctl enable --now docker
```

### 6. Verify Docker Installation

```bash
sudo docker --version
sudo docker ps
```

### 7. Clone the GitHub Repository on EC2

```bash
git clone https://github.com/MansiPandey-git/cloud-pra.git
cd cloud-pra
```

### 8. Build the Docker Image on EC2

```bash
sudo docker build -t cloud-pra:v1 .
```

### 9. Deploy the Website Container

```bash
sudo docker run -d --name cloud-pra-web -p 80:80 cloud-pra:v1
```

### 10. Verify the Deployment

Open the following URL in your browser:

`http://<EC2-PUBLIC-IP>`

The Cloud & DevOps Learning Hub website should appear.

### 11. Useful Docker Commands

Check running containers:

```bash
sudo docker ps
```

List Docker images:

```bash
sudo docker images
```

View container logs:

```bash
sudo docker logs cloud-pra-web
```

Stop the container:

```bash
sudo docker stop cloud-pra-web
```

Start the container again:

```bash
sudo docker start cloud-pra-web
```

## Key Learnings

- Created and managed a Git repository using Git and GitHub.
- Built a Docker image using a Dockerfile.
- Ran a containerized Nginx website locally.
- Installed and verified Docker on an AWS EC2 Ubuntu instance.
- Pulled project source code from GitHub onto EC2.
- Deployed a Docker container and made the website publicly accessible over HTTP.
- Learned basic Docker commands and AWS security group configuration.

## Security Notes

- Never commit private SSH keys, passwords, access tokens, or other credentials to GitHub.
- Restrict SSH access to your own IP address.
- Allow only the network ports required for the project.
- HTTP traffic is unencrypted; HTTPS would be a future improvement.

## Future Improvements

- Integrate Jenkins for CI/CD automation.
- Create a Jenkins Pipeline using a `Jenkinsfile`.
- Automate Docker image builds after GitHub code changes.
- Explore Kubernetes for container orchestration.

## Author

**Mansi Pandey**

GitHub: [MansiPandey-git](https://github.com/MansiPandey-git)
