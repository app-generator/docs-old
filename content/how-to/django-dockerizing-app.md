---
description: How to setup a Django project to run in Docker
---

# Django Dockerizing App

This page explains how to Dockerize a Django application with ease. For newcomers, Django is a leading web framework crafted in Python and Docker is a virtualization software used to isolate the execution of a  service or product using virtual containers.&#x20;


### Adding Docker

First of all, make sure you have Docker installed and running on your machine. Refer to the official [documentation](https://docs.docker.com/engine/install/) and follow the steps.

Once it's done, create a `Dockerfile` file. This will contains all the commands that could be called on the command line to create an image.

```
# pull official base image
FROM python:3.9.5-slim-buster

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apt-get update \
  && apt-get -y install netcat gcc \
  && apt-get clean

# install python dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# copy project
COPY . .

CMD [ "python", "manage.py migrate" ]
CMD [ "python", "manage.py runserver 0.0.0.0:5000" ]

# Exposing default running port
EXPOSE 5000
```

Once this is done, we can build the image and run it.&#x20;

```bash
$ docker build -t django_app .
$ docker run -p 5000:3000 django_app
```

You can now access your app on localhost:5000.

### Adding Docker Compose

If you want to create multiple images and run them using the precedent Docker configuration, you'll have to create multiple `Dockerfile`.&#x20;

`Docker Compose` saves from this by allowing you to use a `YAML` file to operate multi-container applications at once and run it just with one command.&#x20;

Follow the official [documentation](https://docs.docker.com/compose/install/) to install `docker-compose` on your machine.

Once it's done, create a `docker-compose.yml` file at the root of your project. Make sure to have an `.env` file at the root of your project.&#x20;

```yaml
version: '3.8'

services:
  django-app: # The name of your application
    build: ./
    command: >
      sh -c "python manage.py migrate &&
             python manage.py runserver 0.0.0.0:5000"
    volumes:
      - ./:/usr/src/app/
    ports:
      - 5000:5000
    env_file:
      - ./.env
```

We can now remove some lines from the `Dockerfile`.

```

CMD [ "python", "manage.py migrate" ]
CMD [ "python", "manage.py runserver 0.0.0.0:5000" ]

# Exposing default running port
EXPOSE 5000
```

And now let's use `docker-compose` command to build and run the image.

```
docker-compose up --build
```

And your application will be running on localhost:5000.

### Dockerize a production-ready app

@please refer to the configuration implemented by the reference [Django Codebase](https://github.com/app-generator/boilerplate-code-django-dashboard)

* Django App
  * short info regarding the codebase
* Gunicorn - the WSGI server
  * &#x20;[gunicorn-cfg.py](https://github.com/app-generator/boilerplate-code-django-dashboard/blob/master/gunicorn-cfg.py)
* Nginx - a powerful HTTP proxy&#x20;
  * &#x20;[appseed-app.conf](https://github.com/app-generator/boilerplate-code-django-dashboard/blob/master/nginx/appseed-app.conf)
* Dockerfile
  * How to bundle the information&#x20;
    * short description
    * sample -  [Dockerfile](https://github.com/app-generator/boilerplate-code-django-dashboard/blob/master/Dockerfile)
* Docker-compose
  * included sections - short description
  * sample -  [docker-compose.yml](https://github.com/app-generator/boilerplate-code-django-dashboard/blob/master/docker-compose.yml)

