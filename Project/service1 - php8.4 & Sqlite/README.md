## Introduction
You can below things using this docker
    - PHP 8.4
    - Sqlite
    - Composer

## Do Anything Inside Container
Open terminal and type `docker exec -it chatwood bash` here you can do anything
```
    1. composer install
    2. php artisan migrate 
    etc..
```

**Note :**  

You can given container name in.yml file
container_name: chatwood
and path to your project I use linux system so it give like this `/home/mdsadique/office/support-app-laravel`
```
    volumes:
     - /home/mdsadique/office/support-app-laravel:/var/www/html
```