---
description: >-
  Template boilerplate code used by AppSeed to generate simple starters coded in
  Flask.
---

# Boilerplate Jinja

**Jinja** is basically an engine used to generate HTML or XML returned to the user via an HTTP response. For those who have not been exposed to a templating language before, such languages essentially contain variables as well as some programming logic, which when evaluated \(or rendered into HTML\) are replaced with actual values. 

> Features:

* UI Ready: the starter contains a `production-ready` design
* Render Engine: Flask / [Jinja2](https://jinja.palletsprojects.com/)
* Deployment scripts: Docker, Gunicorn/Nginx, HEROKU

> Links

* [Jinja Boilerplate Code](https://github.com/app-generator/boilerplate-code-jinja) - Source code \(published on Github\)
* [Jinja Boilerplate Code](https://boilerplate-code-jinja.appseed-srv1.com/) - LIVE demo
* [Support](https://appseed.us/support):  via **Github** \(issues tracker\) and [Discord](https://discord.gg/fZC6hup) - 24/7 LIVE Assistance. 
* Sample [Jinja Templates](https://appseed.us/jinja-template) provided by AppSeed

![Jinja - Official Logo.](../.gitbook/assets/jinja-banner.jpg)

### Environment

To use the stater, [Python3](https://www.python.org/) should be installed properly in the workstation. If you are not sure if Python is properly installed, please open a terminal and type `python --version`. The full list with dependencies and tools required to build the app:

* [Python3](https://www.python.org/) - the programming language used to code the app
* [GIT](https://git-scm.com/) - used to clone the source code from the Github repository
* Basic development tools \(g++ compiler, python development libraries ..etc\) used by Python to compile the app dependencies in your environment. 



### Build the Template <a id="build-the-app"></a>

To built and start the app locally, follow the steps:

> **Get the source code**

* Download the ZIP from Github Repository
* Using GIT tool in the terminal to clone the source code

> **Change the current directory** to `source code` directory

```text
$ git clone https://github.com/app-generator/boilerplate-code-jinja.git
$ cd boilerplate-code-jinja
$
$ # Virtualenv modules installation (Unix based systems)
$ virtualenv env
$ source env/bin/activate
$
$ # Virtualenv modules installation (Windows based systems)
$ # virtualenv env
$ # .\env\Scripts\activate
$
$ # Install requirements
$ pip3 install -r requirements.txt
$
$ # Set the FLASK_APP environment variable
$ (Unix/Mac) export FLASK_APP=run.py
$ (Windows) set FLASK_APP=run.py
$ (Powershell) $env:FLASK_APP = ".\run.py"
$
$ # Set up the DEBUG environment
$ # (Unix/Mac) export FLASK_ENV=development
$ # (Windows) set FLASK_ENV=development
$ # (Powershell) $env:FLASK_ENV = "development"
$
$ # Run the Jinja Template
$ # --host=0.0.0.0 - expose the app on all network interfaces (default 127.0.0.1)
$ # --port=5000    - specify the app port (default 5000)  
$ flask run --host=0.0.0.0 --port=5000
$
$ # Access the UI in browser: http://127.0.0.1:5000/
```



### Codebase Structure

The project has a simple structure, represented as below:

```text
< PROJECT ROOT >
   |
   |-- app/__init__.py
   |-- app/
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/
   |    |    |
   |    |    |-- includes/                 # Page chunks, components
   |    |    |    |
   |    |    |    |-- navigation.html      # Top bar
   |    |    |    |-- sidebar.html         # Left sidebar
   |    |    |    |-- scripts.html         # JS scripts common to all pages
   |    |    |    |-- footer.html          # The common footer
   |    |    |
   |    |    |-- layouts/                  # App Layouts (the master pages)
   |    |    |    |
   |    |    |    |-- base.html            # Used by common pages like index, UI
   |    |    |    |-- base-fullscreen.html # Used by auth pages (login, register)
   |    |    |
   |    |  index.html                      # The default page
   |    |  login.html                      # Auth Login Page
   |    |  register.html                   # Auth Registration Page
   |    |  page-404.html                   # Error 404 page (page not found)
   |    |  page-500.html                   # Error 500 page (server error)
   |    |    *.html                        # All other pages provided by the UI Kit
   |
   |-- requirements.txt
   |
   |-- run.py
   |
   |-- *************************************

```



### Deployment

 The project comes with a basic configuration for [Docker](https://www.docker.com/), [HEROKU](https://www.heroku.com/), [Gunicorn](https://gunicorn.org/), and [Waitress](https://docs.pylonsproject.org/projects/waitress/en/stable/). 

#### [Docker](https://www.docker.com/) execution

The steps to start the template using Docker:

> **Step \#1** - Clone/download the source code

```text
$ git clone https://github.com/app-generator/boilerplate-code-jinja.git
$ cd boilerplate-code-jinja
```

> Step \#2 - Start the app in Docker

```text
$ sudo docker-compose pull && sudo docker-compose build && sudo docker-compose up -d
```

Visit `http://localhost:5005` in your browser. The app should be up & running.



#### [Heroku](https://www.heroku.com/) Deployment

Steps to deploy on **Heroku**

* [Create a FREE account](https://signup.heroku.com/) on the Heroku platform
* [Install the Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up) that match your OS: Mac, Unix or Windows
* Open a terminal window and authenticate via `heroku login` command
* Clone the sources and push the project for LIVE deployment

```text
$ # Clone the source code:
$ git clone https://github.com/app-generator/boilerplate-code-jinja.git
$ cd boilerplate-code-jinja
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

#### 

