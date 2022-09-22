---
description: >-
  This page explains how to deploy a Flask application on Heroku, the popular
  deployment platform.
---

# Flask Deploy on HEROKU

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

* Basic programming knowledge in [Python](https://www.python.org/)
* Basic Flask knowledge and WSGI concept
* Comfortable using a terminal
* Already familiar with [GIT](https://git-scm.com/) - command-line versioning tool


## What is Flask

Flask is a lightweight WSGI web application framework. It is designed to make getting started quick and easy, with the ability to scale up to complex applications. Classified as a microframework, Flask is written in Python and it does not require particular tools or libraries. It has no database abstraction layer, form validation, or any other components where pre-existing third-party libraries provide common functions.

* [Flask](https://palletsprojects.com/p/flask/) - official website
* [Flask](https://flask.palletsprojects.com/) - official documentation


## What is [HEROKU](https://www.heroku.com/)

Heroku's a _fully managed_ platform that helps developers to deploy apps with ease. Heroku is a cloud-based, fully-managed platform as a service (Paas) for building, running, and managing apps - features:

* Runtime - Heroku empowers developers to deliver products using a CLI, called _Heroku Toolbelt_
* PostgreSQL DBMS - a powerful database already configured to be production-ready
* Automatic scaling - Heroku scales in an instant, both vertically and horizontally.
* Github integration - trigger production builds directly from Github commits

To explain the process, we will use a simple Flask Boilerplate already enhanced for a Heroku deployment.


## Sample Project

_Flask Boilerplate_ is a template codebase used by the **AppSeed** platform to generate [Flask Apps](https://appseed.us/apps/flask-apps) enhanced with a basic set of features like authentication, database, ORM.

As mentioned, the project comes pre-configured for Heroku:

* `runtime.txt` - specify the Python version used by Heroku during the build and deploy
* `Procfile` - configuration file that informs Heroku where to look for the [WSGI](https://docs-old.appseed.us/what-is/wsgi/) interface
* `requirements.txt` - must contain the `gunicorn` module


## [Gunicorn](https://docs.gunicorn.org/en/stable/) module

Gunicorn `Green Unicorn` is a Python WSGI HTTP Server for UNIX. It’s a pre-fork worker model ported from Ruby’s Unicorn project. The Gunicorn server is broadly compatible with various web frameworks, simply implemented, light on server resources, and fairly speedy.

For basic usage please access the [PyPi](https://pypi.org/project/gunicorn/) page or the official [docs](https://pypi.org/project/gunicorn/).



## File  `runtime.txt`

To build the deploy any python-based app, Heroku uses a default Python version or the one specified in the runtime.txt file. Supported environment, as per Heroku official documentation - [Specifying a Python version](https://devcenter.heroku.com/articles/python-support#specifying-a-python-version):

* python-3.8.3
* python-3.7.7
* python-3.8.10 <-- **The Default Version**
* python-2.7.18



### Procfile

Heroku apps include a Procfile that specifies the commands that are executed by the app on startup. As specified in the [official docs](https://devcenter.heroku.com/articles/procfile), the _Procfile_ is always a simple text file that is named Procfile without a file extension.

```
web: gunicorn run:app --log-file=-
```

For our sample, `gunicorn` is called with `run:app` argument.



### How to deploy on HEROKU

* [Create a FREE account](https://signup.heroku.com/) on Heroku platform
* [Install the Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up) that match your OS: Mac, Unix or Windows
* Open a terminal window and authenticate via `heroku login` command
* Clone the sources and push the project for LIVE deployment

The full command list, executed on our sample project.

> **Step #1** - Clone the project from Github

```
$ git clone https://github.com/app-generator/boilerplate-code-flask.git
$ cd boilerplate-code-flask
```

> **Step #2** - Check HEROKU is installed

```
$ heroku -v
heroku/7.25.0 win32-x64 node-v12.13.0 # <-- All good
```

> Step #3 - Login to HEROKU plaform using the terminal

```
$ heroku login
$ # this commaond will open a browser window - click the login button (in browser)
```

> Step #4 - Push LIVE the product

```
$ # Create the Heroku project
$ heroku create
$
$ # Trigger the LIVE deploy
$ git push heroku master
$
$ # Open the LIVE app in browser
$ heroku open
```

At this point, you should be able to visit the app in the browser
