---
description: Short introduction to Flask
---

# What IS Flask

**Flask** is a lightweight **WSGI** web application framework. It is designed to make getting started quick and easy, with the ability to scale up to complex applications. Classified as a microframework, Flask is written in Python and it does not require particular tools or libraries. It has no database abstraction layer, form validation, or any other components where pre-existing third-party libraries provide common functions.

Compared to his older brother [Django](https://www.djangoproject.com/), Flask provides a lightweight codebase and more freedom to the developer. This might be a good thing because you have more freedom in terms of app design and structure but at the same time, this freedom might inject problems when your application becomes complex.



### Set up PC for [Flask](https://palletsprojects.com/p/flask/)

Being a Python framework, Flask requires Python to run and expose his magic. Flask is compatible with Python2, Python3 (the recommended version).

**Install Python**

To get started working with Python3, you’ll need to have access to the Python interpreter (the console, and related tools and libraries). We can accomplish this in several ways:

* Download the installer from the official [download](https://www.python.org/downloads/) page.
* Use a package manager like yum, apt on Linux systems
* Homebrew for MacOS users.
* Build Python from sources, a method used by super-geeks.

### Install Python on Windows

To install Python on our windows workstation, a few simple steps should be followed:

* Navigate to the official [download](https://www.python.org/downloads/) page, using a web browser
* Select the installer that matches the OS (32b or 64b)
* Execute the installer (using the default options, should be enough in most of the cases)
* Test the installation by typing `python --version` in a terminal

### Install Python on Linux

There is a very good chance your Linux distribution has Python installed already, but it probably won’t be the latest version, and it may be Python 2 instead of Python3. To check the installed versions, just type:

```bash
$ python --version
$ python3 --version
```

### Install on CentOS

To install, you should first update your system with the `yum` package manager:

```bash
$ sudo yum install python36u
$ sudo yum install python36u-pip
```

If you still have issues set up your workstation for Python, feel free to join the [Discord](https://discord.gg/fZC6hup) server and ask for support.

**Other useful links**

* [Python 3 Installation & Setup Guide](https://realpython.com/installing-python/) - hosted by RealPython
* [How to install Python](https://realpython.com/installing-python/) - a complete guide for many OS: Fedora, MacOS, Ubuntu



### Install [Flask](https://palletsprojects.com/p/flask/)

To install Flask, we can use `PIP`, the official Python package manager:

```bash
$ pip install Flask
```

During Flask installation, other modules will be installed under-the-hood:

* [Werkzeug](https://palletsprojects.com/p/werkzeug/) implements WSGI, the standard Python interface between applications and servers.
* [Jinja](https://palletsprojects.com/p/jinja/) is a template language that renders the pages your application serves.
* [MarkupSafe](https://palletsprojects.com/p/markupsafe/) comes with Jinja. It escapes untrusted input when rendering templates to avoid injection attacks.
* [ItsDangerous](https://palletsprojects.com/p/itsdangerous/) securely signs data to ensure its integrity. This is used to protect Flask’s session cookie.
* [Click](https://palletsprojects.com/p/click/) is a framework for writing command-line applications. It provides the flask command and allows adding custom management commands.



### [Flask](https://palletsprojects.com/p/flask/) - A minimal Application

To code a super simple app with Flask we need to create a new file `hello.py` and write a few lines of code:

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, from Flask!'
```

Above lines, saved in `hello.py` means:

* `Flask` is imported and become ready to be used&#x20;
* `app` is an object constructed by `Flask` library
* `app` object inherit all Flask magic
* `@app.route` is a `decorator` that define a default route for our app
* When the browser access our app, the message `Hello, from Flask!` will be displayed.

**How to start the app**

To run the application you can either use the flask command or python’s `-m` switch with Flask. Before starting the app, we should export the `FLASK_APP` environment variable:

```bash
$ # Set the FLASK_APP environment variable
$ export FLASK_APP=run.py      # Unix/Mac)
$ set FLASK_APP=run.py         # Windows
$ $env:FLASK_APP = ".\run.py"  # Powershell
```

To effectively start the app, please type:

```bash
$ flask run # this will execute hello.py file
```

By default, Flask will start the app on port **5000** - `http://localhost:5000`. By accessing this local address, we should see the message `Hello, from Flask!`

With this minimal example in mind, we can extend this app with more features. A possible list might be:

* add more routes
* add a database to save relevant information&#x20;
* add static assets to use a Bootstrap style, for instance
* implement an authentication system&#x20;



### [Flask](https://palletsprojects.com/p/flask/) Dashboard Sample

[Flask Dashboard - Black](https://appseed.us/admin-dashboards/flask-dashboard-black) is a simple, open-source Flask starter coded with basic modules, database and deployment scripts for Docker, HEROKU and Gunicorn.

**App Features**

* UI Kit: **Black Dashboard** (Free version) provided by **Creative-Tim**
* Modular design with **Blueprints**
* SQLite, PostgreSQL, SQLAlchemy ORM
* Alembic (DB schema migrations)
* Session-Based authentication (via \*\*flask\_login

**App Links**

* [Flask Dashboard - Black Design](https://appseed.us/admin-dashboards/flask-dashboard-black) - Product page
* [Flask Dashboard Black Demo](https://flask-dashboard-black.appseed.us/) - LIVE app

![Flask Dashboard - Black Design, dashboard screen.](https://raw.githubusercontent.com/app-generator/flask-black-dashboard/master/media/flask-black-dashboard-screen.png)
