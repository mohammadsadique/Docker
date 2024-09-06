# Docker Basics

## Introduction
Docker is a platform for developing, shipping, and running applications inside containers. Containers bundle your application with all its dependencies and configurations, ensuring consistency across different environments.

## Install Docker  
   First, install `Docker` from its official website: [Docker Official Website](https://www.docker.com/).

## Graphical Representation

```
Step 1: 📄 Create a Dockerfile
         (This file defines what’s inside your image)

                     ↓

Step 2: 🛠️ Run the build command to create an image  
          (docker build -t your-image-name:version .) 

                     ↓

Step 3: 📦 The image is created  

                     ↓

Step 4: ▶️ Run the image to create a container  
          (docker run -d --name containerName -p 1000:80 your-image-name:version) 

                     ↓

Step 5: 🏠 The container is created and running your project
            (Container is running your project)
```

## Creating a Dockerfile
To understand the basics of Docker, you'll need a single file named `Dockerfile`.

1. Create a file named `Dockerfile` (no extension).
2. Inside the `Dockerfile`, add the following lines of code:

   ```Dockerfile
   FROM php:8.3-apache

   COPY . /var/www/html
   # Dot (.) represent target php page
   # /var/www/html represent container's web directory
   
   EXPOSE 80
   ```

   ```
   |----------------------------------------------------------------------|
   |                           File Structure                             |
   |----------------------------------------------------------------------|
   |                                                                      |
   |    COPY . /var/www/html                                              |
   |    Copies all files from the current directory to /var/www/html      |
   |                                                                      |
   | 📁 project/                                                          |
   |    ├── 📄 Dockerfile                                                 |
   |    ├── 📄 index.php                                                  |
   |                                                                      |
   |                                                                      |
   |----------------------------------------------------------------------|
   |                                                                      |
   |    COPY ./app /var/www/html                                          |
   |    Copies only the 'app/' folder to /var/www/html                    |
   |                                                                      |
   | 📁 project/                                                          |
   |    ├── 📄 Dockerfile                                                 |
   |    ├── 📁 app/                                                       |
   |        └── 📄 index.php                                              |
   |                                                                      |
   |----------------------------------------------------------------------|
   ```
### Building the Docker Image

After creating the `Dockerfile`, build the Docker image with the following command run in the terminal:

```bash
docker build -t your-image-name:version .

# -t = tag
# :version (optional)
# . = The . at the end of the docker build command tells Docker to look for the Dockerfile in the current directory.
```

### Running the Docker Image
Run the image to create a container with:
```bash
docker run -d --name containerName -p 1000:80 your-image-name:version

# -d = detached mode (Run container in the background)
# --name containerName = Names of the container (optional)
# -p = port
# 1000 = it define local port which i want to use to run my project
# 80 =  Its used by container to serve apache
```
And now finally you are ready to run your project.

Access your project at:  http://localhost:1000/
