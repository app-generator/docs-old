---
description: A comprehensive introduction to Django for beginners
---

# Django For Beginners

This tutorial aims to help beginners getting started with Django, a popular Web Framework written in Python.  To get maximum from this content, the audience should be familiar with a terminal and have a minimal set of tools already installed. [Python3](https://www.python.org/), a modern code editor \([VsCode](https://code.visualstudio.com/), [Atom](https://atom.io/)\), and [GIT](https://git-scm.com/) versioning command-line tool should be enough to experiment with all the code.

### Install Python

The core of dependency for Django is Python and we should install the interpreter first. Most of the systems come with Python already installed and we can easily check in the terminal:

```text
$ python --version
Python 3.8.4       <-- All Good     
```

If the version displayed in the terminal is Python2, please note that this version [has been discontinued](https://www.python.org/doc/sunset-python-2/) for versioning and development since Jan.2020. To download and install Python access the [official page](https://www.python.org/downloads/), select the installer that matches the operating system, and follow the installation setup. Once the process is finished, recheck the Python version in the terminal. 

### Manage Dependencies 

With **Python** up and running, we can install Django and other modules required by our development. The recommended way to install and manage the dependencies for a Python project is to use a virtual environment, a safe way to isolate the dependencies across multiple projects. 

```text
$ # Linux-based systems
$ virtualenv env
$ source env/bin/activate  
```

For Windows-based systems, the syntax is slightly different:

```text
$ virtualenv env
$ .\env\Scripts\activate
```

> Let's install Django, using PIP \(official package manager for Python\)

```text
$ pip install django
```

The above command will install the latest stable version of Django. From this point, we can use all tools provided by Django to create a new project, apps and manage the project via Django CLI. 

### Install a Code Editor

This section has plenty of options from the old-school \(yet modern\) [Vim](https://www.vim.org/download.php) to [VsCode](https://code.visualstudio.com/) and [Atom](https://atom.io/). For those unfamiliar with any of these tools, VsCode might be a good choice to get started fast. 

* [VSCode](https://code.visualstudio.com/) - official website
* [VSCode](https://code.visualstudio.com/Download) - download page

![Programming Kit - VSCode editor.](../../.gitbook/assets/programming-kit-vscode.jpg)

### Build a Django Project

A new project can be generated with ease in Django by using _django-admin_ that provides a collection of settings for the database, Django, and security layer.

> Create the project folder

```bash
$ mkdir my-django-project
$ cd my-django-project
```

   Inside the directory, we will generate the core of our project using _django-admin tool :_

```text
$ django-admin startproject config .
```

   **Note**: Take into account that `.` at the end of the command_._ 

> Create the database and the app tables

```text
$ python manage.py makemigrations
$ python manage.py migrate
```

> Start the application

```text
$ python manage.py runserver 
$
$ # Access the web app in browser: http://127.0.0.1:8000/
```

At this point we should see the default Django page in the browser: 

![Django - Default Project Page.](../../.gitbook/assets/django-framework-cover-xs.png)

### Create New Application

In the previous section, we've generated the core of the project that handles the configuration and now we will create the first Django application to serve a simple page to the users. 

```text
$ python manage.py startapp app
```

> Add a new route - edit `app/views.py`

```python
from django.shortcuts import render
from django.http import HttpResponse     # <-- NEW

def hello(request):                      # <-- NEW    
    return HttpResponse("Hello Django")  # <-- NEW   
```

The next step is to inform Django that we've created a new app and update the routing to include the new definition. 

> Update the configuration to include the new app - `core/settings.py`

```python
# File: config/settings.py (partial content)
...
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'app'                           # <-- NEW
]
...
```

> Update the routing rules as below - `core/urls.py`

```python
# File: config/urls.py (partial content)
...
from django.contrib import admin
from django.urls import path
from django.conf.urls import include, url   # <-- NEW
from app.views import hello                 # <-- NEW

urlpatterns = [
    path('admin/', admin.site.urls),
    url('', hello),                         # <-- NEW
]
```



