---
description: A comprehensive introduction to Django Template System
---

# Django Templates

This page explains in deep the template engine used by Django to serve dynamic pages. For newcomers, **Django** is a high-level Python Web framework that encourages rapid development by reusing modules and libraries built by experienced programmers. On top of this, **Django** is actively supported by an impressive [open-source](https://github.com/django/django) community. Github stats: 2k contributors, Used by **675k** Users, ~**58k** Stars. For more information, feel free to access the official website or the short introduction provided by AppSeed:

* [Django](https://www.djangoproject.com/) - official website
* [What is Django](../what-is/django.md) - a comprehensive introduction to Django

![Django Framework - Cover Image.](../../.gitbook/assets/django-framework-cover-xs.png)

Before you can start using Django Template System, you must first install some software on our workstation: Python, and of course, Django. 

> Install Python

The best way to install Python is to access the [download page](https://www.python.org/downloads/) and use the appropriate installer that matches the operating system. Once the installation process is completed we can check if Python is properly installed directly in the terminal:

```text
$ python
Python 3.8.4 (tags/v3.8.4:dfa645a, Jul 13 2020, 16:46:45) ...
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

 The next step is to install Django using a virtual environment: 

```text
$ virtualenv env
$ source env/bin/activate
$
$ pip install django
```

> Create a simple Django project

Once Python and Django are installed, we can move forward in developing a Django application by creating a Django _project_.

```text
$ django-admin startproject django_templates
```

This command will automatically create a `django_templates` folder in the current directory, and all the necessary files for a basic, but fully functioning **Django** website with an SQLite database. Being a `batteries-included` framework, Django scaffolds the project with usable authentication and administration modules out-of-the-box. To use ann these default features a migration should be executed to create the necessary tables. 

```text
$ python manage.py migrate
```

Our new Django project can be started using the command:

```text
$ python manage.py runserver
```

By default, Django embedded server starts on port `8000`. 

### Django Templates Layer

The default configuration generated can be found in the `settings.py` file and should look quite similar to this code chunk: 

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```







### Resources

* [Django’s Templates](https://djangobook.com/mdj2-django-templates/) **-** a ****free chapter from `The Django Book` ****
* [Django Templates](https://www.geeksforgeeks.org/django-templates/) - a really nice article provided by GeeksForGeeks platform



