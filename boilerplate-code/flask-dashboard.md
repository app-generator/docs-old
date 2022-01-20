---
description: >-
  Reference codebase used in all Flask Dashboards provided by the AppSeed
  platform
---

# Boilerplate Flask Dashboards

Open-Source codebase used by all [Flask Dashboards](https://appseed.us/admin-dashboards/flask) provided by AppSeed.

* `Up-to-date` dependencies: **Flask 2.0.2**
* [SCSS compilation](flask-dashboard.md#recompile-css) via Gulp
* Bootstrap 5 Design: [Volt Dashboard](https://flask-volt-dashboard.appseed-srv1.com) (demo link)
* DBMS & Tools: SQLite / PostgreSQL / SQLAlchemy ORM, Flask-Migrate
* Modular design with Blueprints
* `Session-Based authentication` (via flask\_login), Forms validation
* `Deployment`: [Docker](flask-dashboard.md#start-in-docker), Gunicorn / Nginx, HEROKU
* Free [Support](https://appseed.us/support) via Github (issues tracker) and [Discord](https://discord.gg/fZC6hup).

> Links

* [Source Code](https://github.com/app-generator/boilerplate-code-flask-dashboard) - released on Github (MIT License)
* Product [ROADMAP](https://github.com/app-generator/boilerplate-code-flask-dashboard/blob/master/README.md#product-roadmap):
  * [x] `Up-to-date dependencies`
  * [x] Improved `authentication`:
    * [x] Password reset, Email confirmation on register
  * [x] `Extended user model`: custom fields: Name, Surname, Address, User Photo
  * [ ] `API` via Flask-RestX
  * [ ] `Data Tables` - paginated information
  * [ ] `Sample Charts`
  * [ ] `Social Login` for Google and Github
  * [x] `Deployment`:
    * [x] Docker
    * [ ] HEROKU, AWS Ec2, Google Cloud, Azure
  * [ ] `Payments`: One-time payments via [Stripe Checkout](https://stripe.com/payments/checkout)

## Environment <a href="#environment" id="environment"></a>

To use the stater, [Python3](https://www.python.org) should be installed properly in the workstation. If you are not sure if Python is properly installed, please open a terminal and type `python --version`. The full list with dependencies and tools required to build the app:

* [Python3](https://www.python.org) - the programming language used to code the app
* [GIT](https://git-scm.com) - used to clone the source code from the Github repository
* Basic development tools (g++ compiler, python development libraries ..etc) used by Python to compile the app dependencies in your environment.

## Start in Docker <a href="#start-in-docker" id="start-in-docker"></a>

The project comes with Docker support that allows a quick start in any environment

> **Step #1** - Get the source code

* Download the ZIP from the product page
* Use `GIT` tool in the terminal to clone the source code

```bash
$ git clone https://github.com/app-generator/boilerplate-code-flask-dashboard
$ cd boilerplate-code-flask-dashboard
```

> **Step #2** - Execute Docker `commands`

```bash
$ docker-compose up --build  
```

Visit `http://localhost:85` in your browser. The app should be up & running.

> Note: for `Linux-based` systems the above commands might require `sudo` execution. Here is a sample:

```bash
$ sudo docker-compose up --build 
```

## Build the app <a href="#build-the-app" id="build-the-app"></a>

To build and start the app locally, follow the steps:

> **Step #1** - Get the source code

* Download the ZIP from the product page
* Using `GIT` tool in the terminal to clone the source code

> **Step #2** - Install modules using a `Virtual Environment`

```bash
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
```

> **Step #3** - Setup environment

```
$ # Set the FLASK_APP environment variable
$ (Unix/Mac) export FLASK_APP=run.py
$ (Windows) set FLASK_APP=run.py
$ (Powershell) $env:FLASK_APP = ".\run.py"
$
$ # Set up the DEBUG environment
$ # (Unix/Mac) export FLASK_ENV=development
$ # (Windows) set FLASK_ENV=development
$ # (Powershell) $env:FLASK_ENV = "development"
```

> **Step #4** - Start the app

```bash
$ # Start the application (development mode)
$ # --host=0.0.0.0 - expose the app on all network interfaces (default 127.0.0.1)
$ # --port=5000    - specify the app port (default 5000)  
$ flask run 
```

At this point, we can visit the app in the browser **`http://127.0.0.1:5000/`**. By default, the app will redirect guest users to the login page. To access the private pages:

* Create a new user using the **registration page**
* Authenticate using the **login page**

## App Codebase (simplified) <a href="#app-codebase-simplified" id="app-codebase-simplified"></a>

Starter uses a simple codebase (no Blueprints) with a structure presented below:

```
< PROJECT ROOT >
   |
   |-- apps/
   |    |
   |    |-- home/                   # The App that serve HTML files
   |    |-- authentication/         # Handles authentication
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>  # CSS files, Javascripts files
   |    |
   |    |-- templates/              # All Templates 
   |    |    |-- includes/          # UI Components
   |    |    |-- layouts/           # Master pages
   |    |    |-- accounts/          # Authentication pages
   |    |    |-- home/              # UI Kit Pages
   |    |    
   |  config.py                     # Set up the app
   |  __init__.py                   # Initialize the app
   |
   |-- requirements.txt             # Dendencies - SQLite storage
   |-- requirements-mysql.txt       # Dendencies - Mysql DMBS
   |-- requirements-pqsql.txt       # Dendencies - PostgreSql DMBS
   |
   |-- Dockerfile                   # Deployment
   |-- docker-compose.yml           # Deployment
   |-- gunicorn-cfg.py              # Deployment   
   |-- nginx                        # Deployment
   |    |-- appseed-app.conf        # Deployment 
   |
   |-- .env                         # Inject Configuration via Environment
   |-- run.py                       # Start the app - WSGI gateway
   |
   |-- ******************************
```

## App Bootstrap Flow <a href="#bootstrap-flow" id="bootstrap-flow"></a>

* `run.py` loads the `.env` file
* Initialize the app using the specified profile: _Debug_ or _Production_
  * If `env.DEBUG` is set to _True_ the SQLite storage is used
  * If `env.DEBUG` is set to _False_ the specified DB driver is used (MySql, PostgreSQL)
* Call the app factory method `create_app` defined in `apps/**init**.py`
* Redirect the guest users to Login page
* Unlock the pages served by _home_ blueprint for authenticated users

> **`.env`** (saved in the root of the project)

```
# File: `.env`

DEBUG=True              # Enable/Disable the development environment

SECRET_KEY=S3cr3t_Key   # The Key used by Flask to encrypt session information

# Database production settings (If DEBUG=False)

DB_ENGINE=postgresql    # DBMS
DB_NAME=appseed-flask   # Database Name
DB_HOST=localhost       # Database Host
DB_PORT=5432            # Database Port
DB_USERNAME=appseed     # DB Username
DB_PASS=pass            # DB Password
```

> **`run.py`** (simplified version)

```
# File: run.py

DEBUG = config('DEBUG', default=True)

# Create the WSGI app, using the app factory pattern
app = create_app( app_config )

# Migrate automatically the app using Flask Migrate library
Migrate(app, db)
```

> **`apps/__init__.py`** (simplified version)

```
# File: apps/__init__.py

db            = SQLAlchemy()        # Invoke SQLAlchemy
login_manager = LoginManager()      # Invoke Login Manager

def register_extensions(app):
    db.init_app(app)                # Inject SQLAlchemy magic
    login_manager.init_app(app)     # Add Login Manager to the app

# Register app blueprints: `authentication`, `home`
def register_blueprints(app):
    for module_name in ('authentication', 'home'):
        module = import_module('app.{}.routes'.format(module_name))
        app.register_blueprint(module.blueprint)

# Create the tables (automatically)
def configure_database(app):

    @app.before_first_request
    def initialize_database():
        db.create_all()

# Create the WSGI app using the factory pattern
def create_app(config):
    app = Flask(__name__)
    app.config.from_object(config)
    register_extensions(app)
    register_blueprints(app)
    configure_database(app)
    return app
```

The **`apps/__init__.py`** constructs the app by putting together a short-list of things:

* Invoke SQLAlchemy
* Invoke and inject the `Login Manager` into the app
* Load the configuration from `config.py` file
* Register the app blueprints
* Check if the database tables are created
* return the WSGI app

## App Codebase <a href="#app-codebase" id="app-codebase"></a>

The starter defines two blueprints:

* _Home_ blueprint - serve HTM pages for authenticated users
* _Authentication_ blueprint - handles the `login`, `logout`, and `registration` flow

> **Apps / Authentication Blueprint** structure

```
< PROJECT ROOT >
   |
   |-- apps/
   |    |
   |    |-- authentication/     # Handles auth routes (login and register)
   |         |-- routes.py      # Define authentication routes  
   |         |-- models.py      # Defines models  
   |         |-- forms.py       # Define auth forms (login and register) 
   |
   |-- **************************
```

> **Apps / Home Blueprint** structure

```
< PROJECT ROOT >
   |
   |-- apps/
   |    |
   |    |-- home/                          # A simple app that serve HTML files
   |    |    |-- routes.py                 # Define app routes
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component
   |         |    |-- sidebar.html         # Sidebar component
   |         |    |-- footer.html          # App Footer
   |         |    |-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                   # Master pages
   |         |    |-- base-fullscreen.html  # Used by Authentication pages
   |         |    |-- base.html             # Used by common pages
   |         |
   |         |-- accounts/                  # Authentication pages
   |         |    |-- login.html            # Login page
   |         |    |-- register.html         # Register page
   |         |
   |         |-- home/                      # UI Kit Pages
   |              |-- index.html            # Index page
   |              |-- 404-page.html         # 404 page
   |              |-- *.html                # All other pages
   |
   |
   |-- **************************************
```

## Recompile CSS <a href="#recompile-css" id="recompile-css"></a>

To recompile SCSS files, follow this setup:

> **Step #1** - Install tools

* [NodeJS](https://nodejs.org/en/) 12.x or higher
* [Gulp](https://gulpjs.com) - globally
  * `npm install -g gulp-cli`
* [Yarn](https://yarnpkg.com) (optional)

> **Step #2** - Change the working directory to `assets` folder

```bash
$ cd apps/static/assets
```

> **Step #3** - Install modules (this will create a classic `node_modules` directory)

```bash
$ npm install
// OR
$ yarn
```

> **Step #4** - Edit & Recompile SCSS files

```bash
$ gulp scss
```

The generated files are saved in `static/assets/css` directory.

## App Configuration <a href="#app-configuration" id="app-configuration"></a>

The configuration file **`apps/config.py`** defines a dual configuration controlled via the `.env` file ( `DEBUG` variable)

> **Debug Config** - default configuration used for development

This configuration becomes active if `.env` file has the `DEBUG` file set to _True_

```
# Development/Debug configuration

# Set up the App SECRET_KEY
SECRET_KEY = config('SECRET_KEY', default='S#perS3crEt_007')

# This will create a file in <app> FOLDER
SQLALCHEMY_DATABASE_URI = 'sqlite:///' + os.path.join(basedir, 'db.sqlite3')
SQLALCHEMY_TRACK_MODIFICATIONS = False
```

During the first request, the SQLite database and tables are automatically created in the root in the project.

> _Hint_: to visualize the SQLite database content an external tool should be installed: [DB Browser for SQLite](https://sqlitebrowser.org) it might be a good choice.

> **Production Config** - production configuration

This configuration becomes active if `.env` file has the `DEBUG` file set to _False_

```
# Production configuration

SESSION_COOKIE_HTTPONLY  = True
REMEMBER_COOKIE_HTTPONLY = True
REMEMBER_COOKIE_DURATION = 3600

# PostgreSQL database
SQLALCHEMY_DATABASE_URI = '{}://{}:{}@{}:{}/{}'.format(
    config( 'DB_ENGINE'   , default='postgresql'    ),
    config( 'DB_USERNAME' , default='appseed'       ),
    config( 'DB_PASS'     , default='pass'          ),
    config( 'DB_HOST'     , default='localhost'     ),
    config( 'DB_PORT'     , default=5432            ),
    config( 'DB_NAME'     , default='appseed-flask' )
)
```

In this configuration profile, the database defaults to a PostgreSQL DBMS. Make sure the `.env` has the right credentials to access the database.

## App Tables <a href="#app-tables" id="app-tables"></a>

The file **`apps/authentication/models.py`** (Base Blueprint) defines the table(s) used by the application. Being a simple starter, by default the following tabes are defined:

* Table #1 - **Users** with fields:
  * Id - Primary key, unique
  * user - Store the username
  * email - The email address
  * password - Hashed password

## App Forms <a href="#app-forms" id="app-forms"></a>

The file **`app/authentication/forms.py`** (Base Blueprint) defines the table(s) used by the application. Being a simple starter, by default the following forms are defined:

* Form #1 - **LoginForm** with fields:
  * username
  * password
* Form #2 - **RegisterForm** with fields:
  * username - used to authenticate
  * email - email address
  * password - used to authenticate

## App Routing <a href="#app-routing" id="app-routing"></a>

The routing rules are defined by _Base_ and _Home_ blueprints as specified below. This is the public zone of the app.

> **Base Blueprint** - routing file `apps/authentication/routes.py`

* `/login` route is resolved by `login()` method
* `/register` route is resolved by `register()` method
* `/logout` route calls the `logout_user()` defined in [flask\_login](https://flask-login.readthedocs.io/en/latest/)

_Registered ERROR handlers_

* 404 Error - Page not found
* 403 Error - Access Forbidden
* 500 Error - Internal Error

> **Home Blueprint** - routing file `apps/home/routes.py`

This blueprint will serve requested pages from `apps/home/templates` directory to authenticated users. The authentication status is checked by `@login_required` decorator.

* `/<template>` route resolved by `route_template()`.
  * If a requested page is not found a default 404 page is returned to the user

## Pages & Assets <a href="#pages-assets" id="pages-assets"></a>

Pages and all assets defined in the UI Kits are served by the app using both blueprints:

* _Home Blueprint_ manage the static assets - `apps/authentication/static/assets`
* _Home Blueprint_ store the layout `master pages`, HTML chunks (footer. header, scripts) and `login, registration` pages
* _Base Blueprint_ serve the HTML pages (index, page-404, etc) and the rest of the pages defined in the UI kit.

```
< PROJECT ROOT >
   |
   |-- apps/
   |    |
   |    |-- home/                          # A simple app that serve HTML files
   |    |    |-- routes.py                 # Define app routes
   |    |
   |    |-- authentication/                # Handles auth routes (login and register)
   |    |    |-- routes.py                 # Define authentication routes  
   |    |    |-- models.py                 # Defines models  
   |    |    |-- forms.py                  # Define auth forms (login and register) 
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component
   |         |    |-- sidebar.html         # Sidebar component
   |         |    |-- footer.html          # App Footer
   |         |    |-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                   # Master pages
   |         |    |-- base-fullscreen.html  # Used by Authentication pages
   |         |    |-- base.html             # Used by common pages
   |         |
   |         |-- accounts/                  # Authentication pages
   |         |    |-- login.html            # Login page
   |         |    |-- register.html         # Register page
   |         |
   |         |-- home/                      # UI Kit Pages
   |              |-- index.html            # Index page
   |              |-- 404-page.html         # 404 page
   |              |-- *.html                # All other pages
   |
   |-- ************************************************************************
```

## Data Structures <a href="#data-structures" id="data-structures"></a>

The Flask starter exposes a short-list with data structures used globally across the app:

### `current_user` object <a href="#current_user-object" id="current_user-object"></a>

Constructed by [Flask-Login](https://flask-login.readthedocs.io/en/latest/) can be used to detect if the current request is executed by an authenticated user or not. The object has global visibility and can be used in all app controllers and handlers but also in views.

> **How it works**

`app/authentication/models.py` define the callback functions required by **Flask-Login** library:

```
# File: app/authentication/models.py

@login_manager.user_loader
def user_loader(id):
    return User.query.filter_by(id=id).first()

@login_manager.request_loader
def request_loader(request):
    username = request.form.get('username')
    user = User.query.filter_by(username=username).first()
    return user if user else None
```

> **Usage in contoler** (Sample file)

```
def sample_method(path):

    # Redirect guests users to login page
    if not current_user.is_authenticated:
        return redirect(url_for('login'))
```

> **Usage in view**

```
    <div class="collapse navbar-collapse" id="navigation">
        <ul class="navbar-nav ml-auto">

        <!-- The Usage of <current_user> object -->
        <div data-gb-custom-block data-tag="if"></div>

            <!-- Html chunk rendered for authenticated users-->

            <li class="nav-item">
                <a href="/" class="nav-link text-primary">
                    <i class="tim-icons icon-minimal-left"></i> Back to Dashboard
                </a>
            </li>

        

<div data-gb-custom-block data-tag="else">

            <!-- Html chunk rendered for guests users-->

            <li class="nav-item ">
                <a href="{{ url_for('register') }}" class="nav-link">
                    <i class="tim-icons icon-laptop"></i> Register
                </a>
            </li>
            <li class="nav-item ">
                <a href="{{ url_for('login') }}" class="nav-link">
                    <i class="tim-icons icon-single-02"></i> Login
                </a>
            </li>

        

</div>

        </ul>
    </div>
```



## Links & Resources <a href="#data-structures" id="data-structures"></a>

* Ask for [support](https://appseed.us/support) via email and [Discord](https://discord.gg/fZC6hup)
* [Free Dashboards](https://appseed.us/admin-dashboards/open-source) -  a curated index provided by AppSeed &#x20;
