---
description: Short introduction to uWSGI server and architecture
---

# What IS uWsgi

The **uWSGI** project aims at developing a full stack for building hosting services. Application servers (for various programming languages and protocols), proxies, process managers, and monitors are all implemented using a common API and a common configuration style. Thanks to its pluggable architecture it can be extended to support more platforms and languages.

* [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/) - official documentation



### uWSGI Components

* The Core (implements configuration, processes management, sockets creation, monitoring, logging, shared memory areas, ipc, cluster membership)
* Request plugins (implement application server interfaces for various languages and platforms: WSGI, PSGI, Rack, Lua WSAPI, CGI, PHP, Go …)
* Gateways (implement load balancers, proxies and routers)



### Quickstart for Python

This quickstart will show you how to deploy simple WSGI applications and common web frameworks. In order to start using uWSGI we need the `build-essential python-dev` tooling.

> Install on Debian-based distro

```bash
$ apt-get install build-essential python-dev
```

> Install on CentOS distro

```bash
$ yum install build-essential python-dev
```

###

### Install uWSGI

> Before installing uWSGI module, make sure the workstation has the Python development installed.

```bash
$ # Ubuntu, Debian
$ sudo apt-get install python-dev   # for python2.x installs
$ sudo apt-get install python3-dev  # for python3.x installs
$
$ # CentOS, RHEL
$ sudo yum install python-devel     # for python2.x installs
$ sudo yum install python3-devel    # for python3.x installs
$
$ # Fedora
sudo dnf install python2-devel  # for python2.x installs
sudo dnf install python3-devel  # for python3.x installs
```

> uWSGI Via PIP

```bash
$ pip install uwsgi
```

> Using the network installer

```bash
$ curl http://uwsgi.it/install | bash -s default /tmp/uwsgi
```

###

### Simple uWSGI app

Let’s start with a simple “Hello World” example:

```python
def application(env, start_response):
    start_response('200 OK', [('Content-Type','text/html')])
    return [b"Hello World"]
```

Let's save this minimal app as `hitme.py`

As you can see, it is composed of a single Python function. It is called “application” as this is the default function that the uWSGI Python loader will search for.

> Deploy it on HTTP port 9090

```bash
$ uwsgi --http :9090 --wsgi-file hitme.py
```

In case we need monitoring, the stats subsystem allows you to export uWSGI’s internal statistics as JSON:

```bash
$ uwsgi --http :9090 --wsgi-file hitme.py --master --processes 4 --threads 2 --stats 127.0.0.1:9191
```

By visiting port `9090` in the browser, we should see `Hello World` message served by uWSGI.

###

### uWSGI Resources

* [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/) - the official website
* [What is the point of uWSGI?](https://stackoverflow.com/questions/38601440/what-is-the-point-of-uwsgi)
