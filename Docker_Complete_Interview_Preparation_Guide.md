# Docker Complete Interview Preparation Guide (2 Years Experience)

## 1. What is Docker?

Docker is a containerization platform used to package applications with
dependencies, libraries, configurations, and runtime into lightweight
containers.

### Benefits

-   Consistent environment across machines
-   Faster deployment
-   Application isolation
-   Easy scaling
-   Better resource utilization

------------------------------------------------------------------------

## 2. Docker Architecture

Docker components:

### Docker Client

Used to execute Docker commands.

Examples:

``` bash
docker run
docker build
docker pull
```

### Docker Daemon

Responsible for: - Creating containers - Managing images - Managing
networks - Managing storage

### Docker Registry

Stores Docker images.

Examples: - Docker Hub - AWS ECR

------------------------------------------------------------------------

## 3. Important Docker Terminology

### Image

A blueprint/template used to create containers.

### Container

A running instance of an image.

### Dockerfile

A file containing instructions to create Docker images.

### Registry

A storage location for Docker images.

------------------------------------------------------------------------

## 4. Important Docker Commands

### Images

``` bash
docker images
docker pull image_name
docker rmi image_name
```

### Containers

``` bash
docker ps
docker ps -a
docker run image_name
docker stop container_id
docker start container_id
docker rm container_id
```

### Debugging

``` bash
docker logs container_id
docker exec -it container_id bash
docker stats
docker inspect container_id
```

------------------------------------------------------------------------

## 5. Dockerfile Concepts

Important instructions:

### FROM

Defines the base image.

### WORKDIR

Sets working directory.

### COPY

Copies files into the container.

### RUN

Executes commands during image creation.

### CMD

Command executed when container starts.

### EXPOSE

Documents application port.

Example:

``` dockerfile
FROM node:18

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm","start"]
```

------------------------------------------------------------------------

## 6. Docker Build Process

    Dockerfile
        |
    docker build
        |
    Docker Image
        |
    docker run
        |
    Container

Build:

``` bash
docker build -t my-app .
```

Run:

``` bash
docker run -p 3000:3000 my-app
```

------------------------------------------------------------------------

## 7. Docker Volumes

Containers are temporary. Volumes store persistent data.

Used for: - Database storage - Upload files - Application data

Example:

``` bash
docker volume create myvolume
```

------------------------------------------------------------------------

## 8. Docker Networking

Types:

### Bridge Network

Default Docker network.

### Host Network

Uses host machine network.

### None Network

No network access.

------------------------------------------------------------------------

## 9. Docker Compose

Docker Compose manages multiple containers.

Example:

-   React frontend
-   Node.js backend
-   Database

Commands:

``` bash
docker compose up
docker compose down
```

------------------------------------------------------------------------

## 10. React and Node.js Dockerization

### React Application

Steps: 1. Create Dockerfile 2. Install dependencies 3. Build application
4. Run container

### Node.js Application

Steps: 1. Install dependencies 2. Copy source code 3. Expose port 4.
Start server

------------------------------------------------------------------------

## 11. Multi Stage Docker Build

Benefits:

-   Smaller images
-   Faster deployment
-   Better security

Example:

``` dockerfile
FROM node:18 AS build

WORKDIR /app

COPY . .

RUN npm install
RUN npm run build

FROM nginx

COPY --from=build /app/build /usr/share/nginx/html
```

------------------------------------------------------------------------

## 12. Docker Security

Best practices:

-   Use lightweight images
-   Avoid running containers as root
-   Scan images
-   Update dependencies regularly

------------------------------------------------------------------------

## 13. Docker Debugging

Useful commands:

``` bash
docker logs container_id

docker exec -it container_id bash

docker stats

docker inspect container_id
```

Check: - Environment variables - Ports - Network - Application
configuration

------------------------------------------------------------------------

## 14. Docker Deployment Flow

    Developer
     |
    GitHub
     |
    CI/CD Pipeline
     |
    Docker Build
     |
    Docker Registry
     |
    Server
     |
    Docker Container

------------------------------------------------------------------------

# Docker Interview Questions

## Q1. Difference between Docker Image and Container?

### Image

-   Static blueprint
-   Used to create containers

### Container

-   Running instance of an image

------------------------------------------------------------------------

## Q2. Difference between Docker and Virtual Machine?

### Docker

-   Lightweight
-   Shares host OS
-   Faster startup

### Virtual Machine

-   Includes complete operating system
-   Requires more resources

------------------------------------------------------------------------

## Q3. Why use Docker Compose?

Docker Compose helps manage multiple containers together.

Example: - Frontend - Backend - Database

------------------------------------------------------------------------

## Q4. How to reduce Docker image size?

Answer:

-   Use Alpine images
-   Use multi-stage builds
-   Remove unnecessary packages
-   Add .dockerignore

------------------------------------------------------------------------

## Q5. Container is running but application is not accessible. What will you check?

Check:

-   Port mapping
-   Firewall
-   Application binding
-   Docker logs
-   Environment variables

------------------------------------------------------------------------

# Docker Commands Cheat Sheet

``` bash
docker build
docker run
docker pull
docker ps
docker images
docker stop
docker start
docker rm
docker rmi
docker logs
docker exec
docker inspect
docker stats
docker compose up
docker compose down
```

------------------------------------------------------------------------

# Final Preparation Checklist

For a 2 years experience React + Node.js developer:

-   Docker architecture
-   Images and containers
-   Dockerfile
-   Docker Compose
-   Volumes
-   Networking
-   React Dockerization
-   Node.js Dockerization
-   Debugging
-   Deployment
-   CI/CD basics
