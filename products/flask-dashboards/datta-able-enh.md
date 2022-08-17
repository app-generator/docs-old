---
description: >-
  Dashboard built by AppSeed in Flask on top of Datta Able design - Manual Coded
  Version.
---

# Flask Datta Able ENH

This product is manualy coded on top of the generated version [Datta Able PRO](datta-able-pro.md)

> Version: **1.0.13** - release date `2022-07-20`

* Bootstrap 5 Design, `Light/Dark Mode`, 190 pages, Multiple Layouts 
* `DB Tools`: SQLAlchemy ORM, `Flask-Migrate` (schema migrations)
* `Persistence`: SQLite, MySql 
* `Authentication`: Session Based, Social Login via Github & Twitter
* `Users Management`
  * `Extended user profile`
  * Complete Users management (for `Admins`)
* `API` via Flask-RestX
* `Deployment`: Docker, Flask-Minify (page compression)

> Links

* 👉 [Datta Able Flask PRO](https://appseed.us/product/datta-able-pro/flask/) - product page
* 👉 [Support](https://appseed.us/support): Email and LIVE on [Discord](https://discord.gg/fZC6hup)


## ✨ Environment

To use the starter, [Python3](https://www.python.org) should be installed properly in the workstation. If you are not sure if Python is installed, please open a terminal and type `python --version`. Here is the full list with dependencies and tools required to build the app:

* [Python3](https://www.python.org) - the programming language used to code the app
* [GIT](https://git-scm.com) - used to clone the source code from the Github repository
* Basic development tools (g++ compiler, python development libraries ..etc) used by Python to compile the app dependencies in your environment.
* (Optional) `Docker` - a popular virtualization software


## ✨ Start the app in Docker

> 👉 **Step 1** - Access the [product page](https://appseed.us/product/datta-able-pro/flask/) and download the ZIP (requires a purchase)

```bash
$ # Get the code
$ unzip flask-datta-able-enh.zip
$ cd flask-datta-able-enh
```

> 👉 **Step 2** - Start the APP in `Docker`

```bash
$ docker-compose up --build 
```

Visit `http://localhost:5085` in your browser. The app should be up & running



## ✨ Manual Build

> Download the code - access the [product page](https://appseed.us/product/datta-able-pro/flask/) and download the ZIP (requires a purchase)

```bash
$ # Get the code
$ unzip flask-datta-able-enh.zip
$ cd flask-datta-able-enh
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

> Set Up Database

```bash
# Init migration folder
$ flask db init # to be executed only once         
```

```bash
$ flask db migrate # Generate migration SQL
$ flask db upgrade # Apply changes
```

> Create super admin (the superuser account)

```bash
$ flask create_admin
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

> Set Up Database

```bash
# Init migration folder
$ flask db init # to be executed only once         
```

```bash
$ flask db migrate # Generate migration SQL
$ flask db upgrade # Apply changes
```


> Create super admin (the superuser account)

```bash
$ flask create_admin
```


> Start the app

```bash
$ flask run
```

At this point, the app runs at `http://127.0.0.1:5000/`.


## APP Configuration via `.env` file

> Rename `env.sample` to `.env` and edit the variables:

### Flask `environment variables` (used in development)

* `FLASK_APP=run.py` - run.py is the entry point in the project
* `FLASK_ENV=development`

### `DEBUG` Flag

* `DEBUG`: if `True` the SQLite persistence is used.
  * For production use `False` = this will switch to MySql persistence

### `ASSETS_ROOT` used in assets management

* default value: `/static/assets`

### FTP Settings

This section, once defined, the user is able to change their profile photo. To test the connection, run `flask test_ftp`.

* `FTP_SERVER` - ftp server address
* `FTP_USER` - ftp user
* `FTP_PASSWORD` - ftp password
* `FTP_WWW_ROOT` - the public address used for uploaded assets

### MySql Credentials

This section is used when `DEBUG` is set to `False` (production mode)

* `DB_ENGINE`, default value = `mysql`
* `DB_NAME`, default value = `appseed_db`
* `DB_HOST`, default value = `localhost`
* `DB_PORT`, default value = `3306`
* `DB_USERNAME`, default value = `appseed_db_usr`
* `DB_PASS`, default value = `pass`

### Social Authentication via `Github`

When credentials are defined, the app enables the `LOGIN with Github` button on Sign IN page.

* `GITHUB_ID`=YOUR\_GITHUB\_ID
* `GITHUB_SECRET`=YOUR\_GITHUB\_SECRET

### Social Authentication via `Twitter`

When credentials are defined, the app enables the `LOGIN with Twitter` button on Sign IN page.

* `TWITTER_ID`=YOUR\_GITHUB\_ID
* `TWITTER_SECRET`=YOUR\_GITHUB\_SECRET


## ✨ Application Bootstrap Flow

The entry point of the project is the `run.py` file where the project configuration is bundled. The `most important files` that make the project functional are listed below:

* `run.py` is the application entry point
  * read the `Debug` flag from `.env`
  * import the `db` object from `apps` package
  * import the `create_app` helper from `apps`
* `Flask` application is built by `create_app`
  * If `Debug=True` - SQLite is used (development mode)
  * If `Debug=False` - SQLite is used (production mode)
* Configuration
  * is defined in `apps/config.py`


## ✨ API via `Flask-RestX`

API stands for Application Programming Interface and it is used by various programs to communicate. When browsing the internet, you are using an API. The API takes your request, sends it to the service provider, fetches the response, and sends it back to you.

### `Flask-RestX` Intro

Flask-RestX is an extension for Flask that allows us to build REST APIs faster. It has a collection of tools and decorators to help you describe and expose your API to the Swagger documentation.

> The Swagger UI: `http://localhost:5000/api/`

### Exposed models

> `Products` API
  - Definition: `apps/models/`: **Product Class** 
  - `Definition`: id, name, information, description, price, currency
  - URI: `http://localhost:5000/api/products/`

> `Sales` API
  - Definition: `apps/models/`: **Sale Class** 
  - `Definition`: id, product, state, value, fee, currency, client, payment_type, purchase_date
  - URI: `http://localhost:5000/api/products/`


### How to use the API

The API is secured via an `api_token` generated during the registration process. The value is saved in the `Users` table. 
Once the user is authenticated, the `API_TOKEN` is listed on the dashboard.

- GET requests can be used without the API_TOKEN
- All mutating requests (PUT, DELETE, POST) requires the presence of the API_TOKEN in the header: `Authorization` field

> Swagger UI 

- This visual tool is exposed at address `http://localhost:5000/api/` and provides a fast access to the API

> POSTMAN (3rd party tools) 

- Import the sample [POSTMAN collection](https://github.com/app-generator/flask-datta-able-pro/blob/master/media/api-sample.postman_collection) (saved on Github)
- Replace the `Authorization` value with the `API KEY` listed on your dashboard  
- Query the PRODUCTS API
  - `create`, `update` and `delete` products
- Query the SALES API
  - `create`, `update` and `delete` sales

<br />

## ✨ OAuth for `Github` and `Twitter`

Open Authorization (OAuth) is an authorization framework designed to allow third-party applications to access a user's data or resource. With this protocol, you can sign up and log in via social accounts like GitHub and Twitter.

### `Flask-Dance`

Flask-Dance is an extension that allows developers to create Flask-based applications with the option of authenticating via the OAuth protocol.

### OAuth via Github

To authenticate via GitHub, we must define our credentials in the `.env` file.

* `GITHUB_ID`=YOUR\_GITHUB\_ID
* `GITHUB_SECRET`=YOUR\_GITHUB\_SECRET

To get the credentials above;

1. Go to your GitHub account, navigate to `Settings` -> `Developer Settings` -> `OAuth Apps`
2. Edit the OAuth such that

* Call back URL: `https://localhost:5000/login/github/authorized`
* Homepage URL: `https://localhost:5000`

Once done, generate a `secret key`, and copy & paste it into the `.env` file. Do the same for the Client Id generated by GitHub.

Run the app using `HTTPS`

```
$ flask run --cert=adhoc
```

![Oauth via GitHUB](<../../.gitbook/assets/Image 1.jpg>)

You can log in via the GitHub button.

### OAuth via Twitter

To authenticate via Twitter, we must define our credentials in the `.env` file.

* Sign IN to `Twitter`
* Go to the `Developer Section`
* Create a new APP
* Edit  settings
* Check `OAuth` version: v1 or v2 (recommended)
* Callback URL: `https://localhost:5000/login/twitter/authorized`

Edit the `.env` file and run the app using `HTTPS`

* `TWITTER_ID`=YOUR\_TWITTER\_ID
* `TWITTER_SECRET`=YOUR\_TWITTER\_SECRET

```
$ flask run --cert=adhoc
```

You can log in via the Twitter button.

## 👉 Static Assets

The static assets used by the project (`JS`, `CSS`, `images`) are saved inside the `apps/static/assets` folder. This path can be customized with ease via `ASSETS_ROOT` variable saved in the `.env` file.

> How it works

* `.env` defines the `ASSETS_ROOT` variable
* `apps/config.py` read the value of `ASSETS_ROOT` and defaults to `/static/assets` if not found:

```python
# content of apps/config.py (truncated content)

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

## 🚀 Where to go from here

* 👉 Access the [support](https://appseed.us/support/) page in case something is missing
* 👉 Use [Datta Able Generator](https://appseed.us/generator/datta-able/) to generate a new project
