---
description: Short introduction to HEROKU
---

# What IS Heroku

HEROKU is a popular Platform-as-a-Service provider (PaaS) which makes it easy for developers to deploy apps in different technologies and frameworks using a short learning curve. The platform support all major languages like Python, Ruby, Java, PHP, and popular frameworks: Flask, Django, Express.

To use effectively HEROKU we need to install the CLI, the command line interface that helps us to interact with the deployment platform.

### How to start

* Create a FREE account on [HEROKU](https://signup.heroku.com/) platform
* Install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) that match your OS: Mac, Unix, or Windows
* Open a terminal window and authenticate via HEROKU login command:
  * Type in terminal `heroku login`. This will open a new browser window where the LOGIN action must be confirmed

****

> **HEROKU -** Sign Up page

![HEROKU - Sign Up page](https://raw.githubusercontent.com/app-generator/static/master/docs/heroku-sign-up-page.jpg)

****

> **HEROKU -** Instal CLI

![HEROKU - Instal CLI](https://raw.githubusercontent.com/app-generator/static/master/docs/heroku-install-cli.jpg)

After the installation is complete, open a terminal window and type `heroku -v` to check if HEROKU CLI is usable.

```bash
$ heroku -v
$ heroku/7.42.13 win32-x64 node-v12.16.2
$ # The sample output returned by HEROKU CLI on a Windows PC
```

### HEROKU Sample Deployment

We can see HEROKU in action by using two samples FREE apps provided by AppSeed - [Flask Black Dashboard](https://appseed.us/admin-dashboards/flask-dashboard-black). This popular **Flask** starter is provided with all assets required by HEROKU to be deployed in seconds. The relevant files:

> **Step #1** - Edit `runtime.txt` and specify the Python version to be used

```bash
python-3.6.10
```

> **Step #2** - Edit [Procfile](https://github.com/app-generator/flask-black-dashboard/blob/master/Procfile), the HEROKU app bootstrapper

```bash
web: gunicorn run:app --log-file=-
```

The above line instructs HEROKU to use the Gunicorn WSGI server to execute the WSGI app object, returned by [run.py](https://github.com/app-generator/flask-black-dashboard/blob/master/run.py), located at the root of the project.

```python
# Contents of run.py
from flask_migrate import Migrate
from os import environ
... 
app = create_app( app_config )
Migrate(app, db) 
# At this point, app is the WSGI object that Gunicorn expects.
```

The `gunicorn` module must be also present in the [requirements.txt](https://github.com/app-generator/flask-black-dashboard/blob/master/requirements.txt) file, along with other modules required by the app.

```
flask
flask_login
...
python-decouple
gunicorn          # <--- The magic line
```

With all configuration in place, we can start the deployment by typing a few lines in the terminal.

> **Step - #3** Clone the source code of target project

```bash
$ git clone https://github.com/app-generator/flask-black-dashboard.git
$ cd flask-black-dashboard
```

> **Step - #4** HEROKU Login - this will trigger a new browser window

```bash
$ heroku login
```

> **Step - #5** Create the app in HEROKU platform

```bash
$ # Create the app with a random name
$ heroku create 
$
$ # Create app using a name
$ heroku create you-name-here
```

> **Step - #5** Compile the app in the HEROKU environment

```bash
$ git push heroku master
```

> **Step - #6** Open the app in the browser

```bash
$ heroku open
```

At this point, the sample app should be visible in the browser.

![Flask Dashboard - Black Design, free starter coded in Flask by AppSeed.](https://raw.githubusercontent.com/app-generator/flask-black-dashboard/master/media/flask-black-dashboard-screen.png)

###

### HEROKU troubleshooting

* First, make sure HEROKU CLI is accessible in the terminal. To check this type `heroku -v` in the terminal.
* Make sure the commands are typed inside source code directory
* `heroku create` used with an argument - Make sure that name is available in the HEROKU namespace.



### HEROKU-ready apps

Starters provided by AppSeed are deployment-ready by default for many popular platforms - Docker, HEROKU and Gunicorn/Nginx.

* [Flask Dashboard - Black Design](https://appseed.us/admin-dashboards/flask-dashboard-black), free Flask Dashboard starter
* [Flask Dashboard - Material Design](https://appseed.us/admin-dashboards/flask-dashboard-material-design), free Flask Dashboard starter
* [Flask Dashboard - Datta Able Design](https://appseed.us/admin-dashboards/flask-dashboard-dattaable), free Flask Dashboard starter
* [Flask IraDesign](https://appseed.us/apps/flask-apps/flask-illustrations-iradesign), open-source Flask Application
* [Flask Webpixels](https://appseed.us/apps/flask-apps/flask-illustrations-webpixels), open-source Flask Application
