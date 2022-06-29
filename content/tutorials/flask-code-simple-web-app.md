---
description: Learn how to code a simple web app in Flask.
---

# Flask - Code a simple App

This tutorial aims to help beginners to start coding simple apps using **Flask**, the popular Python framework. Before reading or coding anything suggested in this tutorial, it might be a good idea to access the official Flask resources (docs, quickstart):

* [Flask](https://palletsprojects.com/p/flask/) - the official website
* [Flask Documentation](https://flask.palletsprojects.com/en/1.1.x/)



### What is Flask <a href="#what-is-flask" id="what-is-flask"></a>

**Flask** is a lightweight **WSGI** web application framework. It is designed to make getting started quick and easy, with the ability to scale up to complex applications. Classified as a microframework, Flask is written in Python and it does not require particular tools or libraries. It has no database abstraction layer, form validation, or any other components where pre-existing third-party libraries provide common functions.



### Environment  <a href="#environment" id="environment"></a>

To use the stater, [Python3](https://www.python.org/) should be installed properly in the workstation. If you are not sure if Python is properly installed, please open a terminal and type `python --version`. The full ist with dependencies and tools required to build the app:

* [Python3](https://www.python.org/) - the programming language used to code the app
* [GIT](https://git-scm.com/) - used to clone the source code from the Github repository
* Basic development tools (g++ compiler, python development libraries ..etc) used by Python to compile the app dependencies in your environment.



> Check [Python](https://www.python.org/) version (using the terminal)

```
$ # Check Python version
$ python --version
Python 3.7.2 # <--- All good
```

> Check [GIT](https://git-scm.com/) command tool (using the terminal)

```
$ # Check git
$ git --version
$ git version 2.10.1.windows.1 # <--- All good
```

### &#x20;<a href="#flask-a-minimal-app" id="flask-a-minimal-app"></a>

### Flask - a minimal app <a href="#flask-a-minimal-app" id="flask-a-minimal-app"></a>

The most simple app, coded in Flask, looks like this:

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello from Flask!'
```

We save this source code in `hello.py`. The name is not important, but we will reference the file name in the next section of this tutorial.

> **What this code means**

* Flask module is imported
* the app (WSGI compliant) is constructed by Flask
* a (default) route is defined that returns a friendly message to the user: `Hello from Flask`

When a request is received by our app, usually sent by the browser, the Flask core tries to match the path and execute the right handler.

> **Execute our minimal app**

```
$ export FLASK_APP=hello.py
$ flask run
 * Running on http://127.0.0.1:5000/
```

Please notice that export before we start the app using Flask development server. Flask itself should be informed (via the environment) what file should load and execute. In our sample is `hello.py`.

At this moment, we can visit the app in the browser, on port `5000`, the default port used by Flask to serve apps. To start the app on a different port, we must call Flask using `--port` argument.

```
$ export FLASK_APP=hello.py
$ flask run --port=9999
 * Running on http://127.0.0.1:9999/
```

This time, the app is started on port `9999`.



### Flask Resources

* More [Flask Starters](https://appseed.us/admin-dashboards/flask) provided by AppSeed
* Join the [Discord](https://discord.gg/fZC6hup) community and chat with fellow developers &#x20;
