---
description: >-
  Open-source template for Django admin section styled with Volt Dashboard
  Design (free version)
---

# Django Template Volt

Modern template for **Django admin interface** coded on top of Volt Dashboard (free version) from **Themesberg**. Volt Dashboard is a free and open-source Bootstrap 5 Admin Dashboard featuring over 100 components, 11 example pages, and 3 plugins with Vanilla JS.

* [Django Template Volt](https://pypi.org/project/django-admin-volt/) - PyPi Page
* [Django Volt Dashboard](https://appseed.us/product/volt-dashboard/django/) - Open-source starter that uses the same UI Kit
* [Django Volt Dashboard](https://django-volt-dashboard.appseed-srv1.com) - LIVE Demo


## Why `Django Admin Volt`

* Modern `Bootstrap 5` Design
* `Responsive Interface`
* `Minimal Template` overriding
* `Easy integration`

![Django Admin Volt - Open-source Boostrap 5 Design (mobile view).](https://user-images.githubusercontent.com/51070104/196727476-d12f8ddc-4b41-412b-9b95-df3ee3c01ad4.png)

## Installation

```
$ pip install django-admin-volt
// OR
$ pip install git+https://github.com/app-generator/django-admin-volt.git
```

Add `admin_volt` application to the `INSTALLED_APPS` settings of your Django project `settings.py` file (note it should be before `django.contrib.admin`):

```
    INSTALLED_APPS = (
        ...
        'admin_volt.apps.AdminVoltConfig',
        'django.contrib.admin',
    ) 
```

> Collect static if you are in production environment:

```bash
$ python manage.py collectstatic
```

> Start the app

```bash
$ # Set up the database
$ python manage.py makemigrations
$ python manage.py migrate
$
$ # Create the superuser
$ python manage.py createsuperuser
$
$ # Start the application (development mode)
$ python manage.py runserver # default port 8000
```

Access the `admin` section in the browser: `http://127.0.0.1:8000/`

\


## Screenshots

> **Volt Theme** - `Admin Section`

![Django Admin Volt - Main Django Dashboard screen.](https://user-images.githubusercontent.com/51070104/136143245-85cd8af7-43ea-4956-8fcd-45e307171943.png)

> **Volt Theme** - `Dashboard`

![Django Admin Volt - Template project for Django provided by AppSeed.](https://user-images.githubusercontent.com/51070104/132288100-0c65159f-71a6-41f0-9f55-9544916385ae.jpg)

***

[**Django Admin Volt**](https://github.com/app-generator/django-admin-volt) - Modern Admin Interface provided by [**AppSeed**](https://appseed.us/)
