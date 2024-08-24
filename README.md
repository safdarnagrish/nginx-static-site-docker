# Nginx Static Site Docker

This repository provides a step-by-step guide to creating a Docker image for serving a static website using Nginx. The image is then pushed to Docker Hub for public access, and a container is run from this customized image.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Step-by-Step Guide](#step-by-step-guide)
  - [1. Create a New Directory](#1-create-a-new-directory)
  - [2. Create an HTML File](#2-create-an-html-file)
  - [3. Create a Dockerfile](#3-create-a-dockerfile)
  - [4. Build the Docker Image](#4-build-the-docker-image)
  - [5. Run the Docker Container](#5-run-the-docker-container)
  - [6. Tag and Push the Image to Docker Hub](#6-tag-and-push-the-image-to-docker-hub)
  - [7. Verify on Docker Hub](#7-verify-on-docker-hub)
- [Conclusion](#conclusion)

## Introduction

This project demonstrates how to create and customize a Docker image that serves a static website using Nginx. After building the image, you will learn how to push it to Docker Hub and run it as a container.

## Prerequisites

- Docker installed on your local machine.
- Docker Hub account.
- Basic knowledge of Docker and Nginx.

## Project Structure

```bash
.
├── index.html
└── Dockerfile
```

- **index.html**: A simple HTML file that will be served by the Nginx web server.
- **Dockerfile**: A script containing instructions to build the Docker image.

## Step-by-Step Guide

### 1. Create a New Directory

Create a new directory for your project and navigate into it:

```bash
mkdir nginx-static-site
cd nginx-static-site
```

### 2. Create an HTML File

Create a file named `index.html` in your project directory. This file will contain the HTML content that you want to serve:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Welcome to Nginx!</title>
</head>
<body>
    <h1>Hello from Nginx!</h1>
</body>
</html>
```

### 3. Create a Dockerfile

Create a file named `Dockerfile` in your project directory with the following content:

```dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html
```

This Dockerfile uses the official Nginx image as a base and copies your `index.html` file to the appropriate directory within the image.

### 4. Build the Docker Image

Build your Docker image using the following command:

```bash
docker build -t myapp .
```

This command creates a new Docker image with the tag `myapp` using the Dockerfile in the current directory.

### 5. Run the Docker Container

Run a container from your Docker image with the following command:

```bash
docker run -p 8080:80 myapp
```

This command maps port 8080 on your local machine to port 80 inside the container, allowing you to view your static site at `http://localhost:8080`.

To run the container in detached mode, use:

```bash
docker run -d -p 8080:80 myapp
```

### 6. Tag and Push the Image to Docker Hub

Create a new tag for your Docker image and push it to Docker Hub:

```bash
docker tag myapp safdarnagrish/myapp
docker push safdarnagrish/myapp
```

Replace `safdarnagrish` with your Docker Hub username.

### 7. Verify on Docker Hub

Log in to your Docker Hub account and verify that the image has been successfully pushed and is publicly accessible.

## Conclusion

You have successfully created a Docker image for serving a static website using Nginx, pushed it to Docker Hub, and run it as a container. This project provides a basic foundation for deploying simple static sites using Docker.

For any questions or further enhancements, feel free to contribute or open an issue in this repository.


This README.md file is structured to guide users through the process of building, running, and pushing a Docker image for a static website using Nginx. The repository name is optimized for SEO to reflect the project's purpose clearly.
