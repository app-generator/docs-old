---
description: How To customize Django Admin Interface
---

# Django Customize Admin UI

This page explains how to override Django admin and import a custom template to it. Along with the tutorial, we provide a working sample coded on top of Black Dashboard design (free version) designed by Creative-Tim.

**Links & Resources**

* [Django Black Dashboard](https://appseed.us/admin-dashboards/django-dashboard-black) - the product page
* [Django Admin Black](https://github.com/app-generator/django-admin-black) - admin section customized using Black Design


## The Basics

Django provides default pages for login, registration, 404 and 500 pages (etc) the full list can be found in the `site-packages/django` folder:

```bash
.../site-packages/django/contrib/admin/templates/
│
├── admin/
│   │
│   ├── auth/
│   │   └── user/
│   │       ├── add_form.html
│   │       └── change_password.html
│   │
│   ├── 404.html
│   ├── 500.html
│   ├── actions.html
│   ├── app_index.html
│   ├── base.html
│   ├── base_site.html
│   ├── index.html
│   ├── invalid_setup.html
│   ├── login.html
│   ├── pagination.html
│   ├── popup_response.html
│   └── submit_line.html
│
└── registration/
    ├── logged_out.html
    ├── password_change_done.html
    ├── password_change_form.html
    ├── password_reset_complete.html
    ├── password_reset_confirm.html
    ├── password_reset_done.html
    ├── password_reset_email.html
    └── password_reset_form.html
```

To customize a template, we need to provide the page in a custom templates directory and inform Django to use it. When a template page is used, Django will try to resolve the file by scanning the templates provided by the user and after this step, it defaults to ones provided by the Django core.

### Customize 404 page

The admin templates come in two directories:

* admin is for the model object pages.
* registration is for password changes and logging in and out.

To customize the `404` page, you need to override the right file. The relative path leading to the file has to be the same as the one being overridden. The file you’re interested in is `404.html`.

**Step #1 - Create template directory**

```bash
# Django Root Project <-- you are here
mkdir -p templates/
```

**Step #2 - Update Django Settings**

To use the new templates the project settings file should be updated as bellow to use it.

```python
# core/settings.py
# ...

TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",

        # Add the templates directory to the DIR option:
        "DIRS": [os.path.join(BASE_DIR, "templates"), ],
        "APP_DIRS": True,
        "OPTIONS": {
            "context_processors": [
                "django.template.context_processors.debug",
                "django.template.context_processors.request",
                "django.contrib.auth.context_processors.auth",
                "django.contrib.messages.context_processors.messages",
            ],
        },
    },
]
```

As mentioned before, Django will try to resolve a template file by scanning the directories defined by the user in the settings file. If nothing is found, the default version will be used from `site-packages/django/contrib/admin/templates/` directory.

**Step #3 - Customize 404 page**

The custom version of our 404 page can be easily done by copying the default version from `admin/templates/` directory and save it in the directory created in **Step #2**

```bash
# Django Root Project <-- you are here
vi templates/404.html
```

```markup
<!-- templates/404.html --> 


{% raw %}
{% extends "admin/base_site.html" %}
{% load i18n %}

{% block title %}{% trans 'Page not found' %}{% endblock %}

{% block content %}

<h2>{% trans 'Page not found' %} - Custom File</h2>

<p>{% trans "We're sorry, but the requested page could not be found." %}</p>

{% endblock %}
{% endraw %}
```

Once we save the file, Django will use it when a 404 error case occur when users interacts with our application.

### A complete example

This section explains the process of integrating Black Dashboard design (free version) to style the default admin section for Django.

**Download UI Kit & Assets**

Download your favorite template which usually contains **css**, **js**, **images** and **fonts** files. The sample we are using here (Black Dashboard) can be downloaded from the [product page](https://www.creative-tim.com/product/black-dashboard?AFFILIATE=128200).

![Django Admin Black](https://raw.githubusercontent.com/app-generator/django-dashboard-black/master/media/django-dashboard-black-screen.png)

> Please note that you may have to change the template slightly to do this. Because the relevant template must be usable for Django Admin features.

**Create Your Django Project**

Create a Django project and a new application inside using a descriptive name `admin_black`, for instance.

```bash
$ python manage.py startapp admin_black
```

Create new directories `templates`, `static` and `templatetages` inside. The application folders structure should look as below:

```
admin_black/
    migrations/
        __init__.py
    static/
        # we gonna add something here
    templates/
        # we gonna add something here
    templatetags/
        __init__.py
        # we gonna add something here
    __init__.py
    admin.py
    apps.py
    models.py
    tests.py
    utils.py  # To add public and commonly used functions.
    views.py
```

Add your application (admin\_black) to the INSTALLED\_APPS setting of your Django project settings.py file (note it should be before 'django.contrib.admin'):

```python
INSTALLED_APPS = [
    # ...
    'admin_black.apps.AdminBlackConfig',
    'django.contrib.admin',
]
```

Now your application is ready to add a template. To do this, you need to add your template assets files like **css**, **js**, **images** and **fonts** in your application static folder.

> The folders' structure of this section is completely arbitrary.

```
admin_black/
    ...
    static/
        admin/ # In this section you can override the admin assets file like css, js and etc.
            css/
        admin_black/  # This section is for your template assets. You can choose your own name.
            assets/
                css/
                demo/
                fonts/
                img/
                js/
                scss/
            LICENSE.md
        libs/  # this section is for libs like jQuery, jQuery-confirm or etc
    ...
```

> This is my structure and you can make your own structure.

**Define new Django templates**

In the previous, we added all the required information to our project. Now we want to override the Django admin template and add our template. To do this, you need to know that all Django admin template files are located at:

```python
.../site-packages/django/contrib/admin/templates
```

In this section you will see two folders that include **admin** and **registration**. As it is clear from the name, the **admin** folder is related to the admin templates and the **registration** folder is related to registration, such as _password\_reset\_form.html_, _logged\_out.html_ and etc templates.

In Django admin, to override the templates, just create the same files with the same address in your application. For example, to change the _base.html_, just create such a file in your application:

```
admin_black/
    ...
    templates/
        admin/
            base.html  # change this
        registration/
    ...
```

> Note that you must pay attention to the blocks.

**base.html** is a file that you can start with. All other files import this file to use assets. So, you can add your own template files in it.

> Note you can create your own blocks.

**base.html:** _meta_, _css_, _fonts_ and etc

```markup
<!DOCTYPE html>
<html lang="{{ LANGUAGE_CODE|default:"en-us" }}">

<head>
    <meta charset="utf-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <link rel="apple-touch-icon" sizes="76x76" href="
{% raw %}
{% static "admin_black/assets/img/apple-icon.png" %}">
    <link rel="icon" type="image/png" href="{% static "admin_black/assets/img/favicon.png" %}">

    <title>{% block title %}{% endblock %}</title>

    <link href="https://fonts.googleapis.com/css?family=Poppins:200,300,400,600,700,800" rel="stylesheet"/>
    <link href="https://use.fontawesome.com/releases/v5.0.6/css/all.css" rel="stylesheet">

    {% if LANGUAGE_BIDI %}
        <link href="{% static "admin_black/assets/css/bootstrap-rtl.css" %}" rel="stylesheet"/>
    {% endif %}

    <link href="{% static "admin_black/assets/css/nucleo-icons.css" %}" rel="stylesheet"/>
    <link href="{% static "admin_black/assets/css/black-dashboard.css" %}" rel="stylesheet"/>
    <link href="{% static "admin_black/assets/demo/demo.css" %}" rel="stylesheet"/>
    <link href="{% static "admin_black/assets/css/styles.css" %}" rel="stylesheet"/>

    {% block extrastyle %}{% endblock %}
    {% block extrahead %}{% endblock %}
    {% block blockbots %}
        <meta name="robots" content="NONE,NOARCHIVE">
    {% endblock %}
{% endraw %}

</head>
```

**base.html:** _Javascripts_, _jQuery_ and etc.

```markup
...
<script src="
{% raw %}
{% static "admin_black/assets/js/core/jquery.min.js" %}"></script>
<script src="{% static "admin_black/assets/js/core/popper.min.js" %}"></script>
<script src="{% static "admin_black/assets/js/core/bootstrap.min.js" %}"></script>
<script src="{% static "admin_black/assets/js/plugins/perfect-scrollbar.jquery.min.js" %}"></script>
<script src="{% static "admin_black/assets/js/plugins/chartjs.min.js" %}"></script>
<script src="{% static "admin_black/assets/js/plugins/bootstrap-notify.js" %}"></script>
<script src="{% static "admin_black/assets/js/black-dashboard.min.js" %}"></script>
<script src="{% static "admin_black/assets/demo/demo.js" %}"></script>
<script src="https://cdn.trackjs.com/agent/v3/latest/t.js"></script>
<script src="{% static "admin_black/assets/js/scripts.js" %}"></script>

{% block extrascript %}{% endblock %}
{% endraw %}

</body>
</html>
```

> Note that in sections head and footer I created a new block so that I can make changes to these sections on other pages.

You can also use **templatetags** to provide more customization like a custom `sidebar` and `navigation`. To do this create a new file inside the `templatetags` as below:

```
admin_black/
    ...
    templatetags/
        __init__.py
        admin_black.py
    ...
```

```markup
<!-- sidebar.html -->


{% raw %}
{% load admin_black %}

<div class="sidebar">
    <div class="sidebar-wrapper">
        ...
        {% admin_black_get_menu as app_list %}
        {% if app_list %}
            ...
        {% endif %}
{% endraw %}
        ...
    </div>
</div>
```

This way you can override the Django admin template and import your own template.

#### Links & Resource

* [Django Black Dashboard](https://appseed.us/admin-dashboards/django-dashboard-black) - free Django product that uses the same UI Kit
* Access the [AppSeed](https://appseed.us/) platform for support and more [Django Templates](https://appseed.us/admin-dashboards/django)
