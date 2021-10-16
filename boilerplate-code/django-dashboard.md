---
description: The reference codebase used in all Django Admin Dashboards.
---

# Boilerplate Django Dashboards

Open-source codebase used by all Django Dashboards provided by AppSeed

* Reference Codebase - [Django Dashboard Boilerplate](https://github.com/app-generator/boilerplate-code-django-dashboard)
* Up-to-date [dependencies](https://github.com/app-generator/boilerplate-code-django-dashboard/blob/master/requirements.txt): **Django 3.2.6 LTS **
* SQLite Database, Django Native ORM
* Session-Based Authentication, Forms validation
* Deployment scripts: Docker, Gunicorn/Nginx

> Links

* [Source Code](https://github.com/app-generator/boilerplate-code-django-dashboard) - released on Github (MIT License)
* [Product page](https://appseed.us/boilerplate-code/django-dashboard) - Hosted on AppSeed 
* Samples: [Django Dashboards](https://appseed.us/admin-dashboards/django) section on AppSeed 

> Free [support](https://appseed.us/support) via email and [Discord](https://discord.gg/fZC6hup) - 24/7 LIVE Service

###  <a href="environment" id="environment"></a>

### Environment <a href="environment" id="environment"></a>

To use the stater, [Python3](https://www.python.org) should be installed properly in the workstation. If you are not sure if Python is properly installed, please open a terminal and type `python --version`. The full list with dependencies and tools required to build the app:

* [Python3](https://www.python.org) - the programming language used to code the app
* [GIT](https://git-scm.com) - used to clone the source code from the Github repository
* `Basic development tools` (g++ compiler, python development libraries ..etc) used by Python to compile the app dependencies in your environment. 

###  <a href="build-the-app" id="build-the-app"></a>

### Build the app <a href="build-the-app" id="build-the-app"></a>

To built and start the app locally, follow the steps:

> **Step #1** - Get the source code

* Download the ZIP from [Github](https://github.com/app-generator/boilerplate-code-django-dashboard)
* Using `GIT` tool in the terminal to clone the source code

> **Step #2 - **Install modules

```
```





```
$ # Make sure you are running the commands INSIDE source code directory
$
$ # Virtualenv modules installation (Unix based systems)
$ virtualenv env
$ source env/bin/activate
$
$ # Virtualenv modules installation (Windows based systems)
$ # virtualenv env
$ # .\env\Scripts\activate
$
$ # Install modules - SQLite Storage
$ pip3 install -r requirements.txt
$
$ # Create tables
$ python manage.py makemigrations
$ python manage.py migrate
$
$ # Start the application (development mode)
$ python manage.py runserver # default port 8000
$
$ # Start the app - custom port
$ # python manage.py runserver 0.0.0.0:<your_port>
$
$ # Access the web app in browser: http://127.0.0.1:8000/
```

At this point, we can visit the app in the browser **`http://127.0.0.1:8000/`**. By default, the app will redirect guest users to the login page. To access the private pages:

* Create a new user using the **registration page**
* Authenticate using the **login page**

****

### App Codebase <a href="app-codebase" id="app-codebase"></a>

```
< PROJECT ROOT >
   |
   |-- core/                         # Implements app logic 
   |    |-- settings.py              # Django app bootstrapper
   |    |-- static/
   |    |    |-- <css, JS, images>   # CSS files, Javascripts files
   |    |
   |    |-- templates/               # Templates used to render pages
   |         |
   |         |-- includes/           # HTML chunks and components
   |         |-- layouts/            # Master pages
   |         |-- accounts/           # Authentication pages
   |         |    |-- login.html     # Login page
   |         |    |-- register.html  # Register page
   |         |
   |      index.html                 # The default page
   |     page-404.html               # Error 404 page
   |     page-500.html               # Error 404 page
   |       *.html                    # All other HTML pages
   |
   |-- authentication/               # Handles auth routes (login and register)
   |    |
   |    |-- urls.py                  # Define authentication routes  
   |    |-- views.py                 # Handles login and registration  
   |    |-- forms.py                 # Define auth forms  
   |
   |-- app/                          # A simple app that serve HTML files
   |    |
   |    |-- views.py                 # Serve HTML pages for authenticated users
   |    |-- urls.py                  # Define some super simple routes  
   |
   |-- requirements.txt              # Development modules - SQLite storage
   |
   |-- .env                          # Inject Configuration via Environment
   |-- manage.py                     # Start the app 
   |
   |-- ************************************************************************
```



### The bootstrap flow <a href="the-bootstrap-flow" id="the-bootstrap-flow"></a>

* Django bootstrapper `manage.py` uses `core/settings.py` as the main configuration file
* `core/settings.py` loads the app magic from `.env` file
* Redirect the guest users to Login page
* Unlock the pages served by _app_ node for authenticated users



### App Configuration <a href="app-configuration" id="app-configuration"></a>

The environment configuration file **`.env`** specify a short-list with variables:

* [`SECRET_KEY`](https://docs.djangoproject.com/en/3.0/ref/settings/#secret-key) - Used by Django for [cryptographic signing](https://docs.djangoproject.com/en/3.0/topics/signing/)
* `SERVER` - The public domain/address used in the production environment

```
# File: core/settings.py

...

# SECRET_KEY value is read from `.env` file
SECRET_KEY = config('SECRET_KEY', default='S#perS3crEt_1122')

...

# Load the production server address from `.env` file
ALLOWED_HOSTS = ['localhost', '127.0.0.1', config('SERVER', default='127.0.0.1')]

...

# The SQLite database, located in the root of the project
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

 The default database is [SQLite](https://www.sqlite.org) and the name and physical location can be changed by updating `core/settings.py` The database and associated tables are created during the migration commands, listed in the README file:

```
$ python manage.py makemigrations
$ python manage.py migrate
```



### App Tables <a href="app-tables" id="app-tables"></a>

The tables created by the Django migration are generated by the default modules that handle the authentication, session management, and permissions:

* [`django.contrib.auth`](https://docs.djangoproject.com/en/3.0/ref/contrib/auth/#django-contrib-auth) - Django middleware app that implements authentication
* `django.contrib.sessions` - Django middleware app that implements session management



### App Forms <a href="app-forms" id="app-forms"></a>

The file **`authentication/forms.py`** defines the table(s) used by the application. Being a simple starter, by default the following forms are defined:

* Form #1 - **LoginForm** with fields:
  * username
  * password



* Form #2 - **SignUpForm** with fields:
  * name - The friendly name
  * email - eMail address
  * username - used to authenticate
  * password1 - used to authenticate
  * password2 - password check field



### App Routing <a href="app-routing" id="app-routing"></a>

The settings file **`core/settings.py`** specify the routing file `core/urls.py` via _ROOT_URLCONF_ variable:

```
# File: core/settings.py
...

ROOT_URLCONF = 'core.urls'

...
```

> **`core/urls.py`** file

The core routing file aggregates the routing from all apps defined in the project:

```
# File: core/urls.py

urlpatterns = [
    # Django admin routes - inherited from Django default modules
    path('admin/', admin.site.urls),

    # Authentication routes - login / register
    # exposed by `authentication` app
    path("", include("authentication.urls")),

    # App routes - the modules that serve the UI Kit pages
    path("", include("app.urls"))
]

```

###  <a href="pages-assets" id="pages-assets"></a>

### Pages & Assets <a href="pages-assets" id="pages-assets"></a>

Pages served by the starter are organized using a simple folder structure:

```
< PROJECT ROOT >
   |
   |-- core/                               # Implements app logic and serve the static assets
   |    |
   |    |-- static/assets/
   |    |    |-- css
   |    |    |-- JS
   |    |    |-- images
   |    |    |-- SCSS
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component
   |         |    |-- sidebar.html         # Sidebar component
   |         |    |-- footer.html          # App Footer
   |         |    |-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                  # Master pages
   |         |    |-- base-fullscreen.html # Used by Authentication pages
   |         |    |-- base.html            # Used by common pages
   |         |
   |         |-- accounts/                 # Authentication pages
   |         |    |-- login.html           # Login page
   |         |    |-- register.html        # Register page
   |         |
   |      index.html                       # The default page
   |     page-404.html                     # Error 404 page
   |     page-500.html                     # Error 404 page
   |       *.html                          # All other HTML pages
   |
   |-- app/                                # A simple app that serve HTML files
   |    |
   |    |-- views.py                       # Serve HTML pages for authenticated users
   |    |-- urls.py                        # Define some super simple routes  
   |
   |-- ************************************************************************
```

#### Static Assets <a href="static-assets" id="static-assets"></a>

The folder that contains all assets provided by the UI Kit is located in the `core` directory

* `static/assets` - the root directory for all files (JS, images)
* `static/assets/css` - CSS files that style the app
* `static/assets/img` - Images and Icons
* `static/assets/js` - javascript files provided by the UI Kit
* `static/assets/scss` - SCSS files, if provided by the UI Kit vendor

#### `Templates` Folder <a href="templates-folder" id="templates-folder"></a>

All pages served by the application are located inside this folder.

* `templates/layouts` - the directory with app master pages (layouts)
* `templates/includes` - the directory with HTML chunks and components
* `templates/accounts` - store the authentication pages (login, registration)
* `templates/` - all pages defined/served by the app are saved at the root of the `templates` folder

#### Common pages <a href="common-pages" id="common-pages"></a>

This section lists the common pages defined in all Flask applications prototyped on top of this generic starter.

* login.html, rendered with `layouts/base-fullscreen.html`
* register.html, rendered with `layouts/base-fullscreen.html`
* index.html, rendered with `layouts/base.html`
* page-404.html, rendered with `layouts/base.html`
* page-403.html, rendered with `layouts/base.html`

### Data Structures <a href="data-structures" id="data-structures"></a>

The starter exposes a short-list with data structures used globally across the app:

#### `request.user` object <a href="requestuser-object" id="requestuser-object"></a>

Constructed by [AuthenticationMiddleware](https://docs.djangoproject.com/en/3.0/ref/middleware/#django.contrib.auth.middleware.AuthenticationMiddleware) can be used to detect if the current request is executed by an authenticated user or not. The object has global visibility and can be used in all app controllers and handlers but also in views.

> **Usage in controller**

```
# Sample File

from django.http import HttpResponse

def testme(path):

    # Redirect guests users to login page
    if request.user.is_authenticated:
        return HttpResponse("User authenticated")
    else:
        return HttpResponse("Access forbidden - please authenticate")
```

> **Usage in view**

```
    <div class="collapse navbar-collapse" id="navigation">
        <ul class="navbar-nav ml-auto">

        <!-- The Usage of <current_user> object -->
        {% if request.user.is_authenticated %}

            <!-- Html chunk rendered for authenticated users-->

            <li class="nav-item">
                <a href="/" class="nav-link text-primary">
                    <i class="tim-icons icon-minimal-left"></i> Your Dashboard
                </a>
            </li>

        {% else %}

            <!-- Html chunk rendered for guests users-->

            <li class="nav-item ">
                <a href="{% url 'register' %}" class="nav-link">
                    <i class="tim-icons icon-laptop"></i> Register
                </a>
            </li>
            <li class="nav-item ">
                <a href="{% url 'login' %}" class="nav-link">
                    <i class="tim-icons icon-single-02"></i> Login
                </a>
            </li>

        {% endif %}

        </ul>
    </div>
```

