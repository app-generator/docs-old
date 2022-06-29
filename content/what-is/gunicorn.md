---
description: Short introduction to Gunicorn
---

# What IS Gunicorn

[Gunicorn](https://gunicorn.org/) 'Green Unicorn' is a Python WSGI HTTP Server for UNIX. It's a pre-fork worker model. The Gunicorn server is broadly compatible with various web frameworks, simply implemented, light on server resources, and fairly speedy.

Gunicorn is one of many WSGI server implementations, but it's particularly important because it is a stable, commonly-used part of web app deployments that's powered some of the largest Python-powered web applications in the world, such as Instagram.

Gunicorn is based on a pre-fork worker model, compared to a worker model architecture. The pre-work worker model means that a master thread spins up workers to handle requests but otherwise does not control how those workers perform the request handling. Each worker is independent of the controller.



### Gunicorn Features

* Natively supports WSGI, Django, and Paster
* Automatic worker process management
* Simple Python configuration
* Multiple worker configurations
* Various server hooks for extensibility
* Compatible with Python 3.x >= 3.4



### Gunicorn Installation

> Requirements: Python 3.x >= 3.4

To install the latest released version of Gunicorn

```bash
$ pip install gunicorn
```

From sources

```bash
$ pip install git+https://github.com/benoitc/gunicorn.git
```

###

### Basic Setup Sample

```python
$ pip install gunicorn
$ cat myapp.py
    def app(environ, start_response):
        data = b"Hello, World!\n"
        start_response("200 OK", [
            ("Content-Type", "text/plain"),
            ("Content-Length", str(len(data)))
        ])
        return iter([data])
$ gunicorn -w 4 myapp:app
```

###

### Resources

* [Gunicorn](https://gunicorn.org/) - the official website
* [Gunicorn Docs](http://docs.gunicorn.org/en/stable/) - for the last stable version
* [Gunicorn](https://www.fullstackpython.com/green-unicorn-gunicorn.html) - blog article published on `Full-Stack Python`
