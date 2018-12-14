## Laravel deployment with Docker

### Features
- nginx 1.15
- php 7.3
- Mysql 5.7
- redis 5.0

### Instalation
Just copy the [app.docker](https://github.com/jpcanoso/docker-laravel/raw/master/app.docker), [docker-compose.yml](https://github.com/jpcanoso/docker-laravel/raw/master/docker-compose.yml), [vhost.conf](https://github.com/jpcanoso/docker-laravel/raw/master/vhost.conf) and [web.docker](https://github.com/jpcanoso/docker-laravel/raw/master/web.docker) files to your laravel project source directory and run
`$ docker-compose up -d`

OR

```
$ cd laravel-project-source
$ git clone https://github.com/jpcanoso/docker-laravel.git
$ docker-compose up -d
```

### Laravel Setup
#### Mysql
You will need to configure the connection details on the .env file

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=33061
DB_DATABASE=docker
DB_USERNAME=root
DB_PASSWORD=secret
```

#### Redis
First you will need to install the predis package for Laravel

`$ composer require predis/predis`

Then setup your .env file accordingly
```
CACHE_DRIVER=redis
REDIS_HOST=127.0.0.1
REDIS_PORT=63791
```

### Ports
IMAGE | Ports
----- | -----
NGINX | 8080->80
PHP   | 9000
MYSQL | 33061->3306
REDIS | 63791->6379

### Customization
All the ports can be changed on [docker-compose.yml](https://github.com/jpcanoso/docker-laravel/raw/master/docker-compose.yml) file.
The nginx version can be changed on the [web.docker](https://github.com/jpcanoso/docker-laravel/raw/master/web.docker) file.
Check the supported versions [here](https://hub.docker.com/_/nginx/)

The php version can be changed on the [app.docker](https://github.com/jpcanoso/docker-laravel/raw/master/app.docker) file.
Check the supported versions [here](https://hub.docker.com/_/php/)

The mysql and redis versions can be changed on the [docker-compose.yml](https://github.com/jpcanoso/docker-laravel/raw/master/docker-compose.yml) file.
Check the supported versions respectively [here](https://hub.docker.com/_/mysql/) and [here](https://hub.docker.com/_/redis/).
