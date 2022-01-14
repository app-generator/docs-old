---
description: How To code a simple Flask Application
---

# Code a simple app In Flask

This page explains how to code a simple [Flask](https://www.palletsprojects.com/p/flask/) application.



### Prerequisites

* Basic programming knowledge in Python
* Basic Flask knowledge
* Comfortable using a terminal



### A minimal app

Before using Flask, we need to install it. Open a terminal and type:

```bash
$ pip install Flask
```

Create a new file **hello.py** with the following content:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return f'Hello from Flask!'
```

Once the file is saved, let's start the app:

```bash
$ # Set up the DEBUG environment
$ # (Unix/Mac) export FLASK_ENV=development
$ # (Windows) set FLASK_ENV=development
$ # (Powershell) $env:FLASK_ENV = "development"
$
$ flask run
$ # Visit the app in browser: http://127.0.0.1:5000/
```

By visiting the app in the browser we should see "Hello from Flask" message.



#### Links & Resources

* More [Flask Apps](https://appseed.us/apps/flask-apps) provided by AppSeed
* More [Flask Dashboards](https://appseed.us/admin-dashboards/flask) - a curated index provided by AppSeed
