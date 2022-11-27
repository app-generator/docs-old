---
description: Open-source sample provided by AppSeed to explain Django routing mechanism.
---

# Django Routing Sample

This sample might be useful to beginners to understand **how the routing system works in Django** Web Framework. In the end, the sample will route three things: a default route that shows a simple _Hello World,_ a 2nd route that displays a random number at each page refresh, and the last route that shows a random image pulled from the internet.


> Resources

* [Django Routing Sample](https://github.com/app-generator/django-routing-sample) - the source code (Github/MIT License)
* More [Django Samples](https://appseed.us/admin-dashboards/django) provided with authentication, basic modules


## What is Django

Django is a high-level Python Web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of Web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.

> Read more about [Django Framework](../../content/what-is/django.md) - quick introduction


## How to code this sample

This sample can be coded from scratch by following the steps below.

> Check [Python](../../content/what-is/python.md) Version

```
$ python --version
Python 3.8.4 <-- All good
```

> Create/activate a virtual environment - Unix-based system

```
$ # Virtualenv modules installation
$ virtualenv env
$ source env/bin/activate  
```

For Windows, the syntax is slightly different

```
$ # virtualenv env
$ # .\env\Scripts\activate
```

> Install Django

```
$ pip install django
```

> Create a new Django Project

```
$ mkdir django-sample-urls
$ cd django-sample-urls
```

Inside the new directory, we will invoke `startproject` subcommand

```
$ django-admin startproject config .
```

**Note**: Take into account that `.` at the end of the command.

> Setup the database

```
$ python manage.py makemigrations
$ python manage.py migrate
```

> Start the app

```
$ python manage.py runserver 
$
$ # Access the web app in browser: http://127.0.0.1:8000/
```

At this point we should see the default Django page in the browser:

![Django - Default Project Page.](../../.gitbook/assets/django-framework-cover.jpg)

> Create a new Django app

```
$ python manage.py startapp sample
```

## **Add a simple route**

Let's edit `sample/views.py` as shown below:

```python
def hello(request): 
    return HttpResponse("Hello Django") 
```

**Configure Django** to use the new route -  update `config/urls.py` as below:

```python
from django.contrib import admin
from django.urls  import path
from django.conf.urls import include, url   # <-- NEW
from sample.views import hello              # <-- NEW

urlpatterns = [
    path('admin/', admin.site.urls),
    url('', hello),                         # <-- NEW
]
```

In other words, the default route is served by `hello` method defined in `sample/views.py.`


## New Route - Dynamic content

Let's create a new route that shows a random number - `sample/views.py`.

```python
...
from random import random
...
def myrandom(request): 
    return HttpResponse("Random - " + str( random() ) ) 
```

The new method invoke `random()` from Python core library, converts the result to a string and returns the result. The browser output should be similar to this:

![Django Routing - Dynamic Content Route.](<../../.gitbook/assets/image (4).png>)


## New Route - Random Images

This route will pull a random image from a public (and free) service and inject the returned content into the browser response. To achieve this goal, we need a new Python library called `requests` to pull the random image with ease.

The controller code should be defined in `sample/views.py`. 

```python
...
import requests
...
def randomimage(request):
    r = requests.get('http://thecatapi.com/api/images/get?format=src&type=png')
    return HttpResponse( r.content, content_type="image/png")
```

To see the effects in the browser, the routing should be updated accordingly.

```python
# Contents of config/urls.py
...
from sample.views import hello, myrandom, randomimage # <-- Updated 
...
urlpatterns = [
    path('admin/'     , admin.site.urls),
    url('randomimage' , randomimage),                 # <-- New
    url('random'      , myrandom),
    url(''            , hello), 
]
```

The browser sample output returned by a local iteration: 

![Django Routing Sample - Browser output](<../../.gitbook/assets/image (5).png>)


## Resources

* Read more about [Django](https://www.djangoproject.com/) (official docs)
* Start fast a new project using _development-ready_ [Django Starters](https://appseed.us/admin-dashboards/django)
