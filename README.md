# Laravel Dockerized

This is a Docker template for a Laravel app.

## Advantages

* Deploy your Laravel app anywhere Docker is supported
* Develop locally without having to install XAMPP or set up virtual hosts
* Easily override `php.ini` and `nginx.conf` parameters through editable files in `nginx/` and `php/`

## Pre-requisites

* Docker (obviously)
* Docker Compose

## Usage

First, you need to clone this repository. Somewhere your IDE can access will be good. Then, create a `src/` directory inside.

If you are using this to **work on a Laravel project**, remove the `.git` folder so you don't connect to this repository:

```
cd laravel-docker
rm -rf .git
```

If you wish to contribute to **this** project (a bug fix, an enhancement, etc.), **don't delete the git folder** so that you can still push changes.

We delete the `.git` folder becauese it's a pain to manage git submodules (your app will live in `src/`).

Then, to run the containers, first you need to build the PHP image (since we also need to bundle `composer` and set the correct user permissions):

```
docker-compose build
```

Then, run them all:

```
docker-compose up -d
```

After your containers have booted, you should now be able to view http://localhost:8080/.

## Loading an app

Place your project inside the `src/` folder. If you want to create a new Laravel app, see the **Running commands** section below.

## Settings

Refer to the `docker-compose.yml` file for more information regarding ports, default passwords and the like.

## Running commands

> Container working directories are automatically set to `src/`.

To create a new project:

```
docker exec -it php composer create-project --prefer-dist laravel/laravel .
```

To run composer commands:

```
docker exec -it php composer <command, e.g. install/update/dump-autoload>
```

To run `artisan`:

```
docker exec -it php php artisan <command, e.g. migrate>
```