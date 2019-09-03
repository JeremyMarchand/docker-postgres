# LAMP stack built with Docker Compose

This is a basic Linux Apache Postgres Php stack environment built using Docker Compose. It consists following:

* PHP 7.2
* Apache 2.4
* Postgres
* PgAdmin 4

## Installation


```shell
git clone git@github.com:JeremyMarchand/docker-postgres.git
cd docker-postgres/
docker-compose up -d
```

Your stack is now ready!! You can access it via `http://localhost`.

## Docker
#### Useful command
* Display running containers
```shell
docker ps
```
* Stop a container
```shell
docker stop ID or Name
```
* Stop all containers
```shell
docker stop $(docker ps -a -q)
```

## Configuration

This package comes with default configuration options. You can modify them by creating `.env` file in your root directory.

To make it easy, just copy the content from `sample.env` file and update the environment variable values as per your need.

### Configuration Variables

There are following configuration variables available and you can customize them by overwritting in your own `.env` file.

_**DOCUMENT_ROOT**_

It is a document root for Apache server. The default value for this is `./www`. All your sites will go here and will be synced automatically.

_**VHOSTS_DIR**_

This is for virtual hosts. The default value for this is `./config/vhosts`. You can place your virtual hosts conf files here.

> Make sure you add an entry to your system's `hosts` file for each virtual host.

_**APACHE_LOG_DIR**_

This will be used to store Apache logs. The default value for this is `./logs/apache2`.

## Web Server

Apache is configured to run on port 80. So, you can access it via `http://localhost`.

#### Apache Modules

By default following modules are enabled.

* rewrite
* headers

> If you want to enable more modules, just update `./bin/webserver/Dockerfile`. You can also generate a PR and we will merge if seems good for general purpose.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.

#### Connect via SSH

You can connect to web server using `docker exec` command to perform various operation on it. Use below command to login to container via ssh.

```shell
docker exec -it 7.2.x-webserver /bin/bash
```

## PHP

The installed version of PHP is 7.2

#### Extensions

By default following extensions are installed.

* mysqli
* mbstring
* pgsql
* zip
* intl
* mcrypt
* curl
* json
* iconv
* xml
* xmlrpc
* gd

> If you want to install more extension, just update `./bin/webserver/Dockerfile`. You can also generate a PR and we will merge if seems good for general purpose.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.

## Redis

It comes with Redis. It runs on default port `6379`.
