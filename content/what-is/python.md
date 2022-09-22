---
description: Short introduction to Python
---

# What IS Python

[Python](https://www.python.org/) is a general-purpose coding language—which means that, unlike HTML, CSS, and JavaScript, it can be used for other types of programming and software development besides web development. Python is interpreted, easy to learn surrounded by a huge ecosystem, actively supported and used in many industries and domains - Resources:

* [Python](https://www.python.org/) - the official website
* [Python For Beginners](https://www.python.org/about/gettingstarted/) - a starting guide &#x20;
* [Python Cheatsheet](https://www.pythoncheatsheet.org/) - this site should make you curious
* [Flask](https://flask.palletsprojects.com/en/1.1.x/) - popular Python web framework&#x20;

**Can be used for things like**: (starting from the simple ones)

* Basic programming: using strings, adding numbers, open files
* Writing system scripts (creating instructions that tell a computer system to “do” something)
* Back end (or server-side) web and mobile app development
* Desktop apps and software development
* Processing big data and performing mathematical computations



### Install Python

The **Python** can be downloaded from the [official website](https://www.python.org/). Choose the installer for your operating system, download, and click a few times. By typing python --version in a terminal window, you should see something like this:

```bash
$ python --version
Python 3.7.2
```

###

### Coding in Python

To start using Python we need to open a terminal, type `python` and we should be see the python console waiting for input.

**Define variables**

```python
>>> a = 'Hello'
```

**Use a variable**

```python
>>> a
'Hello'
```

**Concatenate strings**

```python
>>> a = 'Hello'
>>> b = ' World'
>>> a + b
'Hello World'
```

**Multiply a string**

```python
>>> a = 'more '
>>> a * 2
'more more '
```

**Concatenate a string with a number**

```python
>>> a = 'text '
>>> b = 1
>>> a + b
TypeError: can only concatenate str (not "int") to str
>>>
>>> a + str(b)
'text 1'
```

###

### Install libraries

Python is an open-source software actively supported by a huge ecosystem where programmers expose their work to be reused by others. Flask and Django are just a few examples. The full-index with available packages can be found on [PyPI - Python Package Index](https://pypi.org/).

In this section we will write code to extract the title from a web page. To do this, we will reuse two popular libraries putbished on **PyPI** and use them in the python console to extract the title from `google.com`.

**PIP** is a official package installer for Python and usually is shipped by Python installer.

```bash
$ pip install requests
$ pip install BeautifulSoup4
```

Once the libraries are installed succesfully, we can write code in the Python console. \
&#x20;Just for fun, we can **scan and extract the title** from `Google` site with a few lines of code:

```python
>>> import requests                        # import the library
>>> from bs4 import BeautifulSoup as bs    # import the library
>>> site = 'https://google.com'            # define the website we want to process
>>> page = requests.get( site )            # download the page
>>> soup = bs(page.content, 'html.parser') # Parse the downloaded page with BeautifulSoup
>>> soup.title                             # Print the title   
<title>Google</title>
```

### [Python Web Frameworks](https://hackr.io/blog/python-frameworks)

* [Flask](https://flask.palletsprojects.com/) - Available under the BSD license, Flask is another popular Python framework. Inspired by the Sinatra Ruby framework, the microframework requires Jinja2 library and Werkzeug WSGI toolkit.
* [Django](https://www.djangoproject.com/) - Full-stack framework Django is one of the most beloved web development frameworks for developing Python applications.
* [FastAPI](https://fastapi.tiangolo.com/) - a high performance, easy to learn, ready for production framework

### Resources

* [Flask Dashboards](http://appseed.us/admin-dashboards/flask) - provided by AppSeed
* [Django Dashboards](http://appseed.us/admin-dashboards/django) - a curated list
* Join [AppSeed](https://appseed.us) - For support and `production-ready` starters&#x20;
