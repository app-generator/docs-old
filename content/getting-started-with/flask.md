---
description: A short introduction to Flask for beginners.
---

# Getting Started with Flask

This page aims to help beginners getting started with Flask, a popular Python web framework. For newcomers, **Flask** is a lightweight web application framework designed to make getting started quick and easy, with the ability to scale up to complex applications.

> How to getting started with Flask

The quickest setup is to install [Python3](https://www.python.org/), a code editor like [VsCode](https://code.visualstudio.com/) or [Atom](https://atom.io/), and (optionally) GIT the popular command-line versioning tool.

Once all tools are installed and accessible in the terminal, we can code and start a simple Flask application:

> **Step #1** - Install Flask using [PIP](https://pypi.org/project/pip/)

```
$ pip install Flask
```

> **Step 2** - Create a new file `app.py` with following content:

```python
from flask import Flask 
app = Flask(__name__) 
 
@app.route('/') 
def hello_world(): 
    return 'Hello from Flask!' 
 
if __name__ == '__main__': 
    app.run() 
```

> **Step #3** - Start the app

```
$ python3 app.py
```

By visiting the `http://127.0.0.1:5000/` in the browser, we should see the `Hello World` message served by Flask.


## Resources

* Flask - official website
* A curated list with [Flask Apps](https://appseed.us/apps/flask/) and [dashboards](https://appseed.us/admin-dashboards/flask/) provided by AppSeed
* Ask for [support](https://appseed.us/support/) in case of any issues
