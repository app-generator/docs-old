---
description: Open-source API Server crafted in Flask using JWT Authentication and SQLite.
---

# API Server Flask

Simple [Flask API Boilerplate](https://appseed.us/boilerplate-code/flask-api-boilerplate) enhanced with JWT authentication, SqlAlchemy, **SQLite** persistence and deployment scripts via Docker. It has all the ready-to-use bare minimum essentials.

> Version: **[v1.0.2](https://github.com/app-generator/api-server-flask/releases)**, release date `2022-06-07` 

* [API Definition](api-unified-definition.md) - the unified API structure implemented by this server
* [Flask API Server](https://github.com/app-generator/api-server-flask) - source code
* Full-stack samples compatible with this product:
  * [React Berry Dashboard](https://github.com/app-generator/react-berry-admin-template) - open-source sample
  * [React Datta Dashboard](https://github.com/app-generator/react-datta-able-dashboard) - open-source sample

> API Methods - for full description please access [API Unified Definition](api-unified-definition.md)

* USERS API:
  * `/api/users/register`: create a new user
  * `/api/users/login`: authenticate an existing user
  * `/api/users/logout`: delete the associated JWT token
  * `/api/users/checkSession`: check an existing JWT Token for validity
  * `/api/users/edit` - edit the information associated with a registered user 

![Flask API Server - Open-source Product.](../../.gitbook/assets/api-cover-flask-xs.jpg)


## ✨ Requirements

* **Python3** (Python2 is not supported)
* **Flask**==2.1.2
* **flask-restx**==0.5.1
* **Flask-JWT-Extended**==4.4.1
* pytest


## ✨ Getting Started

> 👉 **Step 1** - clone the project using GIT

```
$ git clone https://github.com/app-generator/api-server-flask.git
$ cd api-server-flask
```

> 👉 **Step 2** - Install dependencies (using a virtual environment)

```
$ python3 -m venv /path/to/your/virtual/environment
$ source <path/to/venv>/bin/activate
```

Install dependencies in once the `virtualenv`  is activated

```
$ pip install -r requirements.txt
```

> 👉 **Step 3** - Prepare the environment

```
$ export FLASK_APP=run.py
$ export FLASK_ENV=development
```

> Or for Windows-based systems

```
$ (Windows CMD) set FLASK_APP=run.py
$ (Windows CMD) set FLASK_ENV=development
$
$ (Powershell) $env:FLASK_APP = ".\run.py"
$ (Powershell) $env:FLASK_ENV = "development"
```

> 👉 **Step 4** - Initialize the database, check `run.py` for shell context

```
$ flask shell
>>> from api import db
>>> db.create_all()
```

> 👉 **Step 5** - Start the API server

```
$ python run.py
// OR
$ flask run
```

Visit `http://localhost:5000` in your browser. The API server will be running.


## ✨ Project Structure

The codebase has a simple, intuitive structure where `run.py` is responsible to bundle and start the API Server using the setup coded by the `api` folder:   

```
api-server-flask/
├── api
│   ├── config.py
│   ├── __init__.py
│   ├── models.py
│   └── routes.py
├── Dockerfile
├── README.md
├── requirements.txt
├── run.py
└── tests.py
```


## ✨ Compatible Fullstack Products

The product can be used as a standalone server but also as an authentication server for React, Vue products. Such a product already configured with Django API Server is [**React Datta Able**](https://appseed.us/product/datta-able/api-server-nodejs/react/)**,** an open-source React Dashboard.

* [React Datta Able](https://appseed.us/product/datta-able/api-server-nodejs/react/) - product page
* 👉 ​[React Datta Able](https://github.com/app-generator/react-datta-able-dashboard) - source code

![React Datta Able - Open-Source Dashboard.](https://gblobscdn.gitbook.com/assets%2F-MYVW6MKCi9iujNc3SK\_%2F-Memyr3wdOIsonokJPUQ%2F-Men-RiulajMsyVGTEgy%2Freact-datta-able-cover.jpg?alt=media\&token=c87fbe5e-44b0-4d3d-9bb3-c41495fbb567)
