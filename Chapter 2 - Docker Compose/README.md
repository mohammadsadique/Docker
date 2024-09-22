# Docker Composer

## Introduction
Docker Compose is a tool used to easily run multiple containers together. 
For example, if you are working on a PHP project that needs both Apache (for the web server) and MySQL (for the database), you can set them up with a `docker-compose.yml` file.

## docker-compose.yml
Create a file named docker-compose.yml. In this file, you define the Docker images you need. For a PHP project, you might use images like `phpmyadmin`, `mysql`, and `apache`.

The `.yml` extension stands for YAML, YAML does have a full form! It originally stood for "Yet Another Markup Language"—but later, the creators decided it was better to call it "YAML Ain't Markup Language". 

You can save YAML files with either the `.yml` or `.yaml` extension! Both are accepted.

## [Docker Hub](https://hub.docker.com/) 
Docker Hub is like a marketplace where you can find the images (pre-built software packages) you need for your project.

When you create a `docker-compose.yml` file, you are setting up an environment for your project. For a PHP project, you might need services like `Apache`, `MySQL`, and `phpMyAdmin`.

You can search  [Docker Hub](https://hub.docker.com/) for images like php, mysql, and phpmyadmin.

For example, if you need PHP 7.3, search for "php" on Docker Hub. You'll find various results, including the official PHP image. To get a specific version, check the `Tags` section.

## Set Up an Environment
Once you have your `docker-compose.yml` file, you can add multiple  services (containers) to it. You can find image names and configurations from Docker's documentation, Github  or even searching on Google or use AI.

Just like in a `Dockerfile` where you define things like the image name, ports, and volumes, you’ll do similar things in your `docker-compose.yml` file.

Here’s a simple example to help you understand:
```
services:

  web:
    image: php:8.3-apache
    ports: 
      - "8000:80"
    volumes:
      - .:/var/www/html
  
  db:
    image: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: "123"

  phpmyadmin:
    image: phpmyadmin
    restart: always
    ports:
      - 8001:80
    environment:
      - PMA_PASSWORD= ""
```

Don’t worry about memorizing the code—you can easily find similar examples in Docker documentation, on Google, or by asking AI!

## Build & Run Docker
When you run the command below in the terminal for the first time, it will `build` and `run` the containers.


If you make changes to the `docker-compose.yml` file,Docker will automatically check for updates.

 - When it `builds`, it pulls the image from the Docker Hub server.

 - When it `runs`,  it starts the containers (without needing to build again) and creates an instance of the image (i.e., it creates a container from the image).


```
docker compose up -d
```

## Application URL
The application runs on http://localhost:8000/ and phpMyAdmin runs at http://localhost:8001/.

