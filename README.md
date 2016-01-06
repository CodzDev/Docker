# Docker - web development

[![Join the chat at https://gitter.im/CodzDev/Docker](https://badges.gitter.im/CodzDev/Docker.svg)](https://gitter.im/CodzDev/Docker?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This repo contains many containers for web development and all with simplicity.

## Web

Package install : `apache2`, `php5`, `curl`, `wget`..

|Variable|Use|
|--------|---|
|`{name}`|Replace  by the name of the container|
|`{path}`|Replace by the path of your project root|
|`{env}`|Replace by a value concerning the Environment variable|

|Environment variable|Use|
|--------------------|---|
|`APACHE_ROOT_PATH`  |Default : `/var/www`|


### Install

Starting a default web container, it's really simple :

`docker run --name {name} -p 80:80 -v {path}:/var/www -d codzdev/web`

Starting a web container, changing the `DocumentRoot` from `apache2` :

`docker run --name {name} -p 80:80 -e APACHE_ROOT_PATH={env} -v {path}:/var/www -d codzdev/web`

### Console access

`docker exec -it {name} bash`

### Stop

`docker stop {name}`

### Remove

`docker remove {name}`

## Database (mysql)

`docker run --name db -p 3306:3306 -v {path}:/var/lib/mysql -d mysql`

Link your web container to mysql container after create `db` container :

`docker run --name {name} --link db -p 80:80 -v {path}:/var/www -d codzdev/web`

## Nodejs

**COMING SOON ..**
