# Docker Getting Started App

This repository documents the basic Docker workflow using the Docker Getting Started sample application.

It includes:

- Cloning the sample app from GitHub
- Creating a Dockerfile
- Building a Docker image
- Pushing the image to Docker Hub
- Pulling the image in another environment
- Running the Docker container
- Checking logs and entering the container

---

## Prerequisites

Install the following tools before starting:

- https://git-scm.com/downloads
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Docker Hub account

Verify the installation:

```powershell
git --version
docker --version

# Docker Getting Started App

This guide demonstrates how to containerize a Node.js application using Docker, push the image to Docker Hub, and run it as a container.

# Docker Getting Started App

This project demonstrates how to containerize a Node.js application using Docker, push the image to Docker Hub, pull it in another environment, and run it as a container.

---

## 1. Clone the Application

Clone the sample application and navigate to the project directory:

```bash
git clone https://github.com/docker/getting-started-app.git
cd getting-started-app
```

---

## 2. Create a Dockerfile

Create an empty file named `Dockerfile`.

### Linux/macOS

```bash
touch Dockerfile
```

### Windows PowerShell

```powershell
notepad Dockerfile
```

Paste the following content into the Dockerfile:

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY . .

RUN yarn install --production

CMD ["node", "src/index.js"]

EXPOSE 3000
```

Save the file.

---

## 3. Build the Docker Image

Build the Docker image using the application code and Dockerfile:

```bash
docker build -t image1 .
```

---

## 4. Verify the Image

Verify that the image has been created and stored locally:

```bash
docker images
```

Example output:

```text
REPOSITORY    TAG       IMAGE ID
image1        latest    xxxxxxxxxxxx
```

---

## 5. Push the Image to Docker Hub

### Login to Docker Hub

```bash
docker login
```

### Tag the Image

Replace `username`, `new-reponame`, and `tagname` with your Docker Hub details.

```bash
docker tag image1:latest username/new-reponame:tagname
```

Verify the tagged image:

```bash
docker images
```

### Push the Image

```bash
docker push username/new-reponame:tagname
```

---

## 6. Pull the Image in Another Environment

```bash
docker pull username/new-reponame:tagname
```

---

## 7. Run the Docker Container

```bash
docker run -dp 3000:3000 username/new-reponame:tagname
```

Explanation:

- `-d` runs the container in detached mode
- `-p 3000:3000` maps local port 3000 to container port 3000

---

## 8. Verify the Application

Open a browser and navigate to:

```text
http://localhost:3000
```

If all steps were completed successfully, the application should be running.

---

## 9. View Running Containers

```bash
docker ps
```

---

## 10. Enter the Running Container

Using container name:

```bash
docker exec -it containername sh
```

Or using container ID:

```bash
docker exec -it containerid sh
```

---

## 11. View Docker Logs

Using container name:

```bash
docker logs containername
```

Or using container ID:

```bash
docker logs containerid
```

---

## Docker Workflow

```text
GitHub Repository
        ↓
    git clone
        ↓
 Application Code
        ↓
    Dockerfile
        ↓
 docker build
        ↓
     image1
        ↓
 docker login
        ↓
 docker tag
        ↓
 docker push
        ↓
   Docker Hub
        ↓
 docker pull
        ↓
 docker run
        ↓
 Application Running
        ↓
 http://localhost:3000
```

---

## Common Commands

```bash
# Build image
docker build -t image1 .

# View images
docker images

# Login
docker login

# Tag image
docker tag image1:latest username/new-reponame:tagname

# Push image
docker push username/new-reponame:tagname

# Pull image
docker pull username/new-reponame:tagname

# Run container
docker run -dp 3000:3000 username/new-reponame:tagname

# View running containers
docker ps

# Enter container
docker exec -it containername sh

# View logs
docker logs containername
```
