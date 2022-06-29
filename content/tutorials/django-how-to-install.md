---
description: The page explains how to install Django using a Virtual Environment
---

# Django - How to Install

Django is a popular framework written in Python used to code modern and secure web applications much faster. Install Django is the first step of this journey and during this short tutorial, we will learn how to properly install Django using a Virtual Environment.&#x20;

> Content Features:

* Level: **beginners**&#x20;
*   Mentioned Topics:

    * Django
    * Virtual Environment
    * Basic command-line commands&#x20;



### What is Django

For newcomers, Django is a popular framework built by experienced developers, actively supported by an impressive open-source community.  Django comes with _batteries included_ concept and provides modules to handle the **database**, **authentication**, **built-in security**, plus a powerful command-line interface to interact with our app. To start learning Django feel free to access:

* [Django](https://www.djangoproject.com/) - the official website and [documentation](https://docs.djangoproject.com/)
* [Django Introduction](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction) - a nice tutorial provided by Mozilla Docs
* [What is Django](../what-is/django.md) - a short introduction provided by AppSeed

![Django Framework - New Project Start Page.](../../.gitbook/assets/django-framework-cover.jpg)



### Virtual Environments

A virtual environment helps us to keep isolated the dependencies used by different Python projects. A simple `use case` might be this one: we have installed locally two Python apps that use different versions of a common library, Django for instance. Without using a virtual environment the only choice is to install the dependencies in the global environment and this might affect the stability and behavior of both apps.&#x20;

A **virtual environment** acts like a sandbox where we can safely install modules with zero effects in the global environment.&#x20;

> Create a new virtual environment

```bash
$ python3 -m venv env
// OR 
$ virtualenv env
```

The above commands have identical effects and will create a new `env` directory in the current working directory.  Once the virtual environment is created, the next step is to run the activation command.

> Activate virtual environment

```
$ # Unix based systems
$ source env/bin/activate
// OR
$ # Windows based systems
$ .\env\Scripts\activate
```

&#x20; On successful activation, the  terminal gets a prefix as below:

```
(env) $
```



### Install Django

The recommended way to install Python packages is to use PIP, the official package manager for Python.&#x20;

```bash
(env) $ # Install latest Django version
(env) $ pip install django 
```

&#x20;The above command will install the latest Django version. To install a specific version, please use the syntax:

```
(env) $ # Install Django 2.2.10
(env) $ pip install "django==2.2.10"
```

&#x20;If all goes well, we can check the version using the Python console:

```python
(env) $ python 
(env) >>> import django
(env) >>> django.__version__
(env) '2.2.10'
```



> How to uninstall Django or any other pachage

The removal of a Python package can be done with ease via `pip`:

```
(env) $ # This will remove Django
(env) $ pip uninstall django
(env) Found existing installation: Django 2.2.10
(env) Uninstalling Django-2.2.10:
(env) ...
(env) Successfully uninstalled Django-2.2.10
```

At this point, Django is no longer available in our virtual environment.&#x20;



### Deactivate Virtual Environment

Once the work is finished, to leave the virtual environment we need to type:

```bash
(env) $ deactivate
```

After running `deactivate` command, the console prefix should be removed by the terminal:

```bash
$ # no environment prefix
```



### Resources

To learn more about Python, **Virtual environments,** or get support, please access:

* [Python](https://www.python.org/) - official website
* [Virtual Environments](https://docs.python.org/3/tutorial/venv.html) - official docs
* Join [AppSeed](https://appseed.us/) and ask for [support](https://appseed.us/support) - for **registered users**&#x20;
