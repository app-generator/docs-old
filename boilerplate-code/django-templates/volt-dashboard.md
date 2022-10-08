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

## Why Django Admin Volt?

* Bootstrap 5 Design: **Volt Dashboard** (Free version) provided by **Themesberg**
* New fresh look
* Responsive mobile interface
* Useful admin home page
* Minimal template overriding
* Easy integration

![Django Template Volt - Open-Source Admin Theme](<../../.gitbook/assets/image (12).png>)

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

> The name respects the convention `APP_NAME.apps.APP_NAMEConfig` required by all apps defined in the **INSTALLED\_APPS** section.

In this feature, we considered that each App can have its own icon, so we ask users to use this feature according to the method. Also in apps.py of each program according to the example add the icon field in the corresponding class. You can go [**here**](https://fontawesome.com/v4.7/icons/) to use more icons.

```
    from django.apps import AppConfig

    class APP_NAMEConfig(AppConfig):
        name = 'APP_NAME'
        icon = 'ICON_CLASS'  # for example: icon = 'fa fa-users'
```

> Make sure `django.template.context_processors.request` context processor is enabled in `settings.py` (Django 1.8+ way):

```python
    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [],
            'APP_DIRS': True,
            'OPTIONS': {
                'context_processors': [
                    ...
                    'django.template.context_processors.request',
                    ...
                ],
            },
        },
    ]
```

> Start the application and connect to the `admin` section using a `superuser` account:

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

At this point, we should be able to access the `admin` section using the new Django Template:

![Django Template Volt - Edit Users Page](<../../.gitbook/assets/image (13).png>)
