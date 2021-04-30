title: How to deploy Flask on Heroku

# [Flask](https://palletsprojects.com/p/flask/) Deploy on [Heroku](https://www.heroku.com/)

This page explains how to deploy a [Flask](https://www.palletsprojects.com/p/flask/) application on Heroku, the popular deployment platform.

<br />

## Prerequisites

- Basic programming knowledge in Python
- Basic Flask knowledge and [WSGI](/what-is/wsgi/) concept
- Comfortable using a terminal
- Already familiar with [GIT](https://git-scm.com/)

<br />

{!info-flask.md!}

{!info-heroku.md!}

To explain the process, we will use a simple Flask Boilerplate already enhanced for a Heroku deployment.

## Sample project - [Flask Boilerplate](https://github.com/app-generator/boilerplate-code-flask)
---

*Flask Boilerplate* is a template codebase used by the **AppSeed** platform to generate [Flask Apps](https://appseed.us/apps/flask-apps) enhanced with a basic set of features:

- UI-Ready, Jinja2 templating
- SQLite database, Flask-SQLAlchemy ORM
- Session-Based auth flow (login, register) via Flask-Login
- Deployment scripts: Docker, Gunicorn / Nginx, Heroku

As mentioned, the project comes pre-configured for Heroku. The relevant files are listed below:

- [runtime.txt](https://github.com/app-generator/boilerplate-code-flask/blob/master/runtime.txt) - specify the Python version used by Heroku during the build and deploy
- [Procfile](https://github.com/app-generator/boilerplate-code-flask/blob/master/Procfile) - configuration file that informs Heroku where to look for the [WSGI](/what-is/wsgi/) interface
- [requirements.txt](https://github.com/app-generator/boilerplate-code-flask/blob/master/requirements.txt) - must contain the `gunicorn` module

<br />

### [Gunicorn](https://docs.gunicorn.org/en/stable/) module
---

Gunicorn `Green Unicorn` is a Python WSGI HTTP Server for UNIX. It’s a pre-fork worker model ported from Ruby’s Unicorn project. The Gunicorn server is broadly compatible with various web frameworks, simply implemented, light on server resources, and fairly speedy.

For basic usage please access the [PyPi](https://pypi.org/project/gunicorn/) page or the official [docs](https://pypi.org/project/gunicorn/).

<br />

### File - [runtime.txt](https://github.com/app-generator/boilerplate-code-flask/blob/master/runtime.txt)
---

To build the deploy any python-based app, Heroku uses a default Python version `python-3.6.10` or the one specified in the runtime.txt file. Supported environment, as per Heroku official documentation - [Specifying a Python version](https://devcenter.heroku.com/articles/python-support#specifying-a-python-version):

- python-3.8.3
- python-3.7.7
- python-3.6.10 <-- **The Default Version**
- python-2.7.18

<br />

### Procfile
---

Heroku apps include a Procfile that specifies the commands that are executed by the app on startup.
As specified in the [official docs](https://devcenter.heroku.com/articles/procfile), the *Procfile* is always a simple text file that is named Procfile without a file extension.

```txt
web: gunicorn run:app --log-file=-
```

For our sample, `gunicorn` is called with `run:app` argument.

<br />

## How to deploy on Heroku

- [Create a FREE account](https://signup.heroku.com/) on Heroku platform
- [Install the Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up) that match your OS: Mac, Unix or Windows
- Open a terminal window and authenticate via `heroku login` command
- Clone the sources and push the project for LIVE deployment

The full command list, executed on our sample project.

```bash
$ # Clone the source code:
$ git clone https://github.com/app-generator/boilerplate-code-flask.git
$ cd boilerplate-code-flask
$
$ # Check Heroku CLI is installed
$ heroku -v
heroku/7.25.0 win32-x64 node-v12.13.0 # <-- All good
$
$ # Check Heroku CLI is installed
$ heroku login
$ # this commaond will open a browser window - click the login button (in browser)
$
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

<br />

## Help & Resources

- Get [support](https://appseed.us/support) via [Discord](https://discord.gg/fZC6hup), in case something is not working
- Read more about Heroku - [official docs](https://devcenter.heroku.com/)
- Check out for more [Flask Apps](https://appseed.us/apps/flask-apps) actively supported by **AppSeed**
- [Flask Admin Dashboards](https://appseed.us/admin-dashboards/flask) - index provided by **AppSeed**

<br />
