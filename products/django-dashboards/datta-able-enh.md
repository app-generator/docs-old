---
description: >-
  Dashboard built by AppSeed in Django on top of Datta Able design - Manual
  Coded Version.
---

# [Datta Able Django ENH](https://appseed.us/product/datta-able-pro/django/)

This product is manualy coded on top of the generated version [Datta Able PRO](datta-able-pro.md)


> Version: **v1.0.9** - release date `2022-07-10`

* UI Kit: [Datta Able PRO](https://appseed.us/product/datta-able/) (Premium version)
* Bootstrap 5 Design (no jQuery dependency)
  * `Light/Dark Mode`
  * 190 pages: `Charts`, Dashboards, `Multiple Layouts`
* SQLite Database, Django Native ORM
* Session-Based Authentication, Forms validation
* Deployment scripts: Docker, Gunicorn/Nginx
* Improved Authentication
  * Visual password strength indicator (registration)
* New Feature: `User Profiles`
  * Extended User profile
  * Added Superusers
  * Image upload via `FTP`

> Links

* 👉 [Datta Able Django PRO](https://appseed.us/product/datta-able-pro/django/) - product page
* 👉 [Datta Able Django PRO](https://django-datta-able-enh.appseed-srv1.com/) - LIVE Demo
* 👉 [Support](https://appseed.us/support) (Email and LIVE on Discord) for `registered users`.

{% embed url="https://www.youtube.com/watch?v=d8OqLGCzOuE" %}
Django Datta Able PRO - Presentation
{% endembed %}

## ✨ Environment

To start with **Datta able ENH ,** [Python3](https://www.python.org/) should be installed properly in the workstation. If you are not sure if Python is installed, please open a terminal and type `python --version`. Here is the full list of dependencies and tools required to build the app:

* [Python3](https://www.python.org/) - the programming language used to code the app.
* [GIT](https://git-scm.com/) - used to clone the source code from the Github repository.
* Basic development tools used by Python to compile the app dependencies in your environment.
* (Optional) [venv](https://docs.python.org/3/library/venv.html) - used to create "lightweight" virtual environments.
* (Optional) [Docker](https://www.docker.com/) - used for OS-level virtualizaton by creating portable packages called containers with all necessary dependencies and configuration.&#x20;

## ✨ Codebase structure

The project structure is simple to understand and intuitive enough as presented below:



```bash
< PROJECT ROOT >
   |
   |-- core/                           # Implements app configuration
   |    |-- settings.py                # Defines Global Settings
   |    |-- wsgi.py                    # Start the app in production
   |    |-- urls.py                    # Define URLs served by all apps/nodes
   |    |-- asgi.py                    # Asynchronous processing of the request
   |    |-- staticfiles                # Collects static resources to be served in production
   |
   |-- apps/
   |    |
   |    |-- home/                      # A simple app that serve HTML files
   |    |    |-- views.py              # Serve HTML pages for authenticated users
   |    |    |-- urls.py               # Define some super simple routes
   |    |    |-- tests.py              # Class-based unit tests
   |    |    |-- models.py             # Classes that map to the database table
   |    |    |-- config.py             # App configuration
   |    |    |-- admin.py              # Customization of Admin panel
   |    |
   |    |-- authentication/            # Handles auth routes (login and register)
   |    |    |-- urls.py               # Define authentication routes  
   |    |    |-- views.py              # Handles login and registration  
   |    |    |-- forms.py              # Define auth forms (login and register) 
   |    |    |-- tests.py              # Class-based authentication unit tests
   |    |    |-- models.py             # Classes that map to the database table
   |    |    |-- config.py             # authentication App configuration
   |    |    |-- apps.py               # authentication App configuration
   |    |    |-- admin.py              # Customization of Admin panel
   |    |
   |    |-- accounts/                  # Manages a User profile
   |    |    |-- admin.py              # Registration of models in admin and 
   |    |    |                         # customizations in Admin panel 
   |    |    |-- apps.py               # accounts App configuration
   |    |    |-- forms.py              # Define profile editing form 
   |    |    |-- models.py             # Classes that map to the database table
   |    |    |-- tests.py              # Class-based unit tests for accounts app
   |    |    |-- urls.py               # Define accounts routes  
   |    |    |-- views.py              # Handles users listing, profile edits, and deleting of accounts  
   |    |
   |    |-- static/
   |    |    |-- assets/
   |    |    |   |-- <css, JS, images> # Various static resource files.
   |    |
   |    |-- templates/                 # HTML templates for various apps
   |    |    |-- account/              # Login, registration and profile templates 
   |    |    |-- home/                 # Chart and dashboard related templates
   |    |    |-- includes/             # Common templates for various apps
   |    |    |-- layouts/              # Base templates for other templates
   |    |
   |    |-- nginx/                     # Implements Nginx configuration 
   |         |-- appseed-app.conf      # Various Nginx  configuration directives
   |
   |-- requirements.txt                # Development modules - SQLite storage
   |
   |-- .env                            # Inject Configuration via Environment
   |-- manage.py                       # Start the app - Django default start script
   |
   |-- ************************************************************************
```



## Improved Authentication

The codebase has been update to support some new features:

* Automatic user suspension on consecutive failed logins
  * Limit saved in `configuration`
  * `Password strength` indicator (registration page)

## FTP Storage

The feature is activated via the `.env` settings. Sample configuration:

```
FTP_UPLOAD=True
upload_cloud_type=storages.backends.ftp.FTPStorage
ftp_username   = <FTP_USER>
ftp_password   = <FTP_PASS>
ftp_server_url = <FTP_SERVER_IP>
ftp_port       = <FTP_SERVER_PORT>
upload_url     = <WWW_ROOT_FOR_IMAGES>
```

## Extended User Profile

* Users are able to edit their profile:
  * Full Name, address, phone number and ZIP Code
* Upload their profile image
  * If the `FTP_UPLOAD` feature is active

## Users Management

> Note: Feature reserved for `superusers`

* List all users
* Edit the information
* Suspend/unsuspend the users

## 🚀 Where to go from here

* 👉 Access the [support](https://appseed.us/support/) page in case something is missing
* 👉 Use [Datta Able Generator](https://appseed.us/generator/datta-able/) to generate a new project
