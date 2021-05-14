---
description: >-
  This page explains how to deploy a Django application on Heroku, the popular
  deployment platform.
---

# Django Deploy on HEROKU

### Prerequisites <a id="prerequisites"></a>

* Basic programming knowledge in [Python](https://www.python.org/)
* Basic Flask knowledge and [WSGI](https://docs-old.appseed.us/what-is/wsgi/) concept
* Comfortable using a terminal
* Already familiar with [GIT](https://git-scm.com/) - command-line versioning tool



### What is Django

 [Django](https://www.djangoproject.com/) is a high-level Python Web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of Web development, so you can focus on writing your app without needing to reinvent the wheel. It's free and open source.

* [Django](https://www.djangoproject.com/) - official website
* [Django](https://docs.djangoproject.com/en/3.2/) - official documentation

### 

### What is [HEROKU](https://www.heroku.com/)

Heroku's a _fully managed_ platform that helps developers to deploy apps with ease. Heroku is a cloud-based, fully-managed platform as a service \(Paas\) for building, running, and managing apps - features:

* Runtime - Heroku empowers developers to deliver products using a CLI, called _Heroku Toolbelt_
* PostgreSQL DBMS - a powerful database already configured to be production-ready
* Automatic scaling - Heroku scales in an instant, both vertically and horizontally.
* Github integration - trigger production builds directly from Github commits

To explain the process, we will use a simple Flask Boilerplate already enhanced for a Heroku deployment.



### Sample Project

_Django Boilerplate_ is a template codebase used by the **AppSeed** platform to generate Django Web Apps enhanced with a basic set of features:

* UI-Ready, simple codebase
* SQLite database, Flask-SQLAlchemy ORM
* Session-Based auth flow \(login, register\) via Flask-Login
* Deployment scripts: Docker, Gunicorn / Nginx, Heroku

As mentioned, the project comes pre-configured for Heroku. The relevant files are listed below:

* [runtime.txt](https://github.com/app-generator/boilerplate-code-django/blob/master/runtime.txt) - specify the Python version used by Heroku during the build and deploy
* [Procfile](https://github.com/app-generator/boilerplate-code-django/blob/master/Procfile) - configuration file that informs Heroku where to look for the [WSGI](https://docs-old.appseed.us/what-is/wsgi/) interface
* [requirements.txt](https://github.com/app-generator/boilerplate-code-django/blob/master/requirements.txt)
* `settings.py` file - to add the required modules provided by the Heroku platform



#### Requirements.txt update <a id="requirementstxt-update"></a>

To have a successful deployment on Heroku, the usual requirements.txt file should be updated to contain some new modules:

* `gunicorn` - the Gunicorn server to start our app
* `django-heroku` - a helper bundle provided by the Heroku development team to make the deployment much easier.



#### File - [runtime.txt](https://github.com/app-generator/boilerplate-code-django/blob/master/runtime.txt) <a id="file-runtimetxt"></a>

To build the deploy any python-based app, Heroku uses a default Python version `python-3.6.10` or the one specified in the runtime.txt file. Supported environment, as per Heroku official documentation - [Specifying a Python version](https://devcenter.heroku.com/articles/python-support#specifying-a-python-version):

* python-3.8.3
* python-3.7.7
* python-3.8.10 &lt;-- **The Default Version**
* python-2.7.18



### How to deploy on HEROKU

* [Create a FREE account](https://signup.heroku.com/) on the Heroku platform
* [Install the Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up) that match your OS: Mac, Unix, or Windows
* Open a terminal window and authenticate via `heroku login` command
* Clone the sources and push the project for LIVE deployment

The full command list, executed on our sample project.

> **Step \#1** - Clone the project from Github

```text
$ git clone https://github.com/app-generator/boilerplate-code-flask.git
$ cd boilerplate-code-flask
```

> **Step \#2** - Check HEROKU is installed

```text
$ heroku -v
heroku/7.25.0 win32-x64 node-v12.13.0 # <-- All good
```

> Step \#3 - Login to HEROKU plaform using the terminal

```text
$ heroku login
$ # this commaond will open a browser window - click the login button (in browser)
```

> Step \#4 - Push LIVE the product

```text
$ # Create the Heroku project
$ heroku create
$
$ # Trigger the LIVE deploy
$ git push heroku master
$
$ # Open the LIVE app in browser
$ heroku open
```

At this point, you should be able to visit the app in the browser. 

