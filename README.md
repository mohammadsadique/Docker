# Docker

Learn `Docker` in a simple way

## Start with the Basics

1. **Install Docker**  
   First, install `Docker` from its official website: [Docker Official Website](https://www.docker.com/).

## Getting Started

To understand the basics of Docker, you'll need a single file named `Dockerfile`.

### Creating a Dockerfile

1. Create a file named `Dockerfile` without any extension.
2. Inside the `Dockerfile`, add the following lines of code:

    ```Dockerfile
    FROM php:8.3-apache

    COPY . /var/www/html

    EXPOSE 80
    ```

### Building the Docker Image

After creating the `Dockerfile`, build the Docker image with the following command:

```bash
docker build -t your-image-name:version

Then run this image to create a container

```bash
docker run -d -p 1000:80 your-image-name:version


1000 = it define local port which i want to use 
80 =  is used by container to serve apache

and now finally you are ready to run your project in 

http://localhost:1000/
