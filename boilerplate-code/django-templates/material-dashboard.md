---
description: >-
  Open-source template for Django admin section styled with Material Dashboard
  Design (free version)
---

# Django Material Dashboard

Modern template for **Django Admin Interface** coded on top of **Material Dashboard**, an open-source `Boostrap 5` design from `Creative-Tim`.

* [Django Template Material](https://pypi.org/project/django-admin-material-dashboard/) - PyPi Page
* [Django Material Dashboard](https://appseed.us/product/material-dashboard/django/) - free starter with the same design
* [Django Material Dashboard](https://django-material-dashboard.appseed-srv1.com/) - LIVE Demo

\


## [Black Friday](https://appseed.us/discounts/) - `75%OFF`

> The campaign is active until `30.NOV` and applies to all products and licenses.

[![AppSeed - Black Friday 2022 Campaign, 75% OFF Discount (all products).](https://user-images.githubusercontent.com/51070104/201829599-9fe6bdd7-3f19-46f3-9115-962eeb13bf29.jpg)](https://appseed.us/discounts/)

\


## Why `Django Admin Material`

* Modern `Bootstrap 5` Design
* `Responsive Interface`
* `Minimal Template` overriding
* `Easy integration`

![Django Admin Material Dashboard - Edit users page.](https://user-images.githubusercontent.com/51070104/169301658-6cf27993-c451-4cd4-9ffa-2968b8981167.png)

## Installation

```
$ pip install django-admin-material-dashboard
// OR
$ pip install git+https://github.com/app-generator/django-admin-material-dashboard.git
```

> Add `admin_material` application to the `INSTALLED_APPS` setting of your Django project `settings.py` file (note it should be before `django.contrib.admin`):

```python
    INSTALLED_APPS = (
        ...
        'admin_material.apps.AdminMaterialDashboardConfig',
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

## Screenshots

> **Material Dashboard Theme** - `Admin Section`

![Django Admin Material Dashboard - Admin dashboard page.](https://user-images.githubusercontent.com/51070104/196743760-6e0e1930-8233-421c-ac53-d65c273b00dc.png)

> **Material Dashboard Theme** - `Admin Widgets`

![Django Admin Material Dashboard - New User Page.](https://user-images.githubusercontent.com/51070104/196743821-2e140dd8-fe15-4615-9e9f-0467900b1a1b.png)

***

[**Django Admin Material**](https://github.com/app-generator/django-admin-material-dashboard) - Modern Admin Interface provided by [**AppSeed**](https://appseed.us/)
