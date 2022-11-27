---
description: >-
  Template boilerplate code used by AppSeed to generate simple starters coded in
  Flask.
---

# Boilerplate Jinja

**Jinja** is basically an engine used to generate HTML or XML returned to the user via an HTTP response. For those who have not been exposed to a templating language before, such languages essentially contain variables as well as some programming logic, which when evaluated (or rendered into HTML) are replaced with actual values.

> Features:

* UI Ready: the starter contains a `production-ready` design
* Render Engine: Flask / [Jinja2](https://jinja.palletsprojects.com)
* Deployment scripts: Docker, Gunicorn/Nginx, HEROKU


## ✨ Environment

To use the starter, [Python3](https://www.python.org) should be installed properly in the workstation. If you are not sure if Python is installed, please open a terminal and type `python --version`. Here is the full list with dependencies and tools required to build the app:

* [Python3](https://www.python.org) - the programming language used to code the app
* [GIT](https://git-scm.com) - used to clone the source code from the Github repository
* Basic development tools (g++ compiler, python development libraries ..etc) used by Python to compile the app dependencies in your environment.
* (Optional) `Docker` - a popular virtualization software


## ✨ Start the app in Docker

> 👉 **Step 1** - Download the code from the GH repository (using `GIT`)

```bash
$ # Get the code
$ git clone https://github.com/app-generator/boilerplate-code-jinja.git
$ cd boilerplate-code-jinja
```

> 👉 **Step 2** - Start the APP in `Docker`

```bash
$ docker-compose up --build 
```

Visit `http://localhost:5085` in your browser. The app should be up & running.


## ✨ Manual Build

> Download the code

```bash
$ # Get the code
$ git clone https://github.com/app-generator/boilerplate-code-jinja.git
$ cd boilerplate-code-jinja
```


### 👉 Set Up for `Unix`, `MacOS`

> Install modules via `VENV`

```bash
$ virtualenv env
$ source env/bin/activate
$ pip3 install -r requirements.txt
```

> Set Up Flask Environment

```bash
$ export FLASK_APP=run.py
$ export FLASK_ENV=development
```

> Start the app

```bash
$ flask run
```

At this point, the app runs at `http://127.0.0.1:5000/`.


### 👉 Set Up for `Windows`

> Install modules via `VENV` (windows)

```
$ virtualenv env
$ .\env\Scripts\activate
$ pip3 install -r requirements.txt
```

> Set Up Flask Environment

```bash
$ # CMD 
$ set FLASK_APP=run.py
$ set FLASK_ENV=development
$
$ # Powershell
$ $env:FLASK_APP = ".\run.py"
$ $env:FLASK_ENV = "development"
```

> Start the app

```bash
$ flask run
```

At this point, the app runs at `http://127.0.0.1:5000/`.


## ✨ Codebase structure

The project is coded using a simple and intuitive structure presented below:

```bash
< PROJECT ROOT >
   |
   |-- apps/
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>          # CSS files, Javascripts files
   |    |
   |    |-- templates/                      # Templates used to render pages
   |    |    |-- includes/                  # HTML chunks and components
   |    |    |    |-- navigation.html       # Top menu component
   |    |    |    |-- footer.html           # App Footer
   |    |    |    |-- scripts.html          # Scripts common to all pages
   |    |    |
   |    |    |-- layouts/                   # Master pages
   |    |    |    |-- base-fullscreen.html  # Used by Authentication pages
   |    |    |    |-- base.html             # Used by common pages
   |    |    |
   |    |    |-- accounts/                  # Authentication pages
   |    |    |    |-- login.html            # Login page
   |    |    |    |-- register.html         # Register page
   |    |    |
   |    |    |-- home/                      # UI Kit Pages
   |    |         |-- index.html            # Index page
   |    |         |-- page-404.html         # 404 page
   |    |         |-- *.html                # All other pages
   |    |    
   |  views.py                              # Implements app routing
   |  config.py                             # Set up the app   
   |    __init__.py                         # Initialize the app
   |
   |-- requirements.txt                     # App Dependencies
   |
   |-- .env                                 # Inject Configuration via Environment
   |-- run.py                               # Start the app - WSGI gateway
   |
   |-- ************************************************************************
```


## ✨ UI Assets and Templates

The project comes with a modern UI fully migrated and usable with Django Template Engine.

### 👉 Page Templates

All pages and components are saved inside the `apps/templates` directory. Here are the standard directories:

* `templates/layouts`: UI masterpages
* `templates/includes`: UI components (used across multiple pages)
* `templates/accounts`: login & registration page
* `templates/home`: all other pages served via a generic routing by `apps/home` app

```bash
< PROJECT ROOT >
   |
   |-- apps/
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>     # CSS files, Javascripts files
   |    |
   |    |-- templates/                 # Templates used to render pages
   |         |-- includes/             # HTML chunks and components
   |         |    |-- navigation.html  # Top menu component
   |         |    |-- footer.html      # App Footer
   |         |    |-- scripts.html     # Scripts common to all pages
   |         |
   |         |-- layouts/              # Master pages
   |         |    |-- base.html        # Used by common pages
   |         |
   |         |-- accounts/             # Authentication pages
   |         |    |-- login.html       # Login page
   |         |    |-- register.html    # Register page
   |         |
   |         |-- home/                 # UI Kit Pages
   |              |-- index.html       # Index page
   |              |-- page-404.html    # 404 page
   |              |-- *.html           # All other pages
   |
   |-- ************************************************************************
```


### 👉 Static Assets

The static assets used by the project (`JS`, `CSS`, `images`) are saved inside the `apps/static/assets` folder. This path can be customized with ease via `ASSETS_ROOT` variable saved in the `.env` file.

> How it works

* `.env` defines the `ASSETS_ROOT` variable
* `core/settings.py` read the value of `ASSETS_ROOT` and defaults to `/static/assets` if not found:

```python
# content of core/settings.py (truncated content)

ASSETS_ROOT = os.getenv('ASSETS_ROOT', '/static/assets') 
```

* All pages and components use the `config.ASSETS_ROOT` variable. Here is a sample extracted from `templates/layouts/base.html`:

```html
<head>

    <!-- Source Code -->
    <link rel="stylesheet" href="{{ config.ASSETS_ROOT }}/css/style.css">

    <!-- RUNTIME -->
    <link rel="stylesheet" href="/static/assets/css/style.css">
```

At runtime, the `href` property is resolved to `/static/assets/css/style.css` based on the value saved in the `.env` file:

```
# No Slash at the end
ASSETS_ROOT=/static/assets
```


## 👉 Static Assets for `production`

As explained in the [Static Assets](boilerplate-jinja.md#static-assets) section, the assets are managed via:

* `apps/static/assets` - the folder where `JS`, `CSS`, and `images` files are saved
* `ASSETS_ROOT` - environment variable, that defaults to `/static/assets` if not defined

In production, the contents of the `apps/static/assets` files should be copied to an external (public) directory and the `ASSETS_ROOT` environment variable updated accordingly.

For instance, if the `static` files are copied to `https://cdn.your-server.com/datta-able-assets`, the `.env` file should be updated as below:

```
# No Slash at the end
ASSETS_ROOT=https://cdn.your-server.com/datta-able-assets
```


## 🚀 Where to go from here

* 👉 Access the [support](https://appseed.us/support/) page in case something is missing
* 👉 Use the [App Generator](https://appseed.us/generator) to generate a new project
