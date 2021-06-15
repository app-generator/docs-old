---
description: A curated index with all Jinja Templates provided by AppSeed
---

# Jinja Templates

[Jinja](https://jinja.palletsprojects.com/en/2.11.x/) is a modern and designer-friendly templating language for Python, modeled after Django’s templates. It is fast, widely used, and secure with the optional sandboxed template execution environment. 

* [Jinja](https://palletsprojects.com/p/jinja/) - official webiste
* [What is Jinja](../../content/what-is/jinja.md) - a comprehensive introduction 

> Jinja Templates - provided by AppSeed

* [Jinja AdminLTE](adminlte.md) - the iconic [AdminLTE](../../content/bootstrap-template/adminlte.md) dashboard now available in Jinja 
* [Jinja Atlantis Lite](atlantis-lite.md) - open-source Bootstrap design
* [Jinja Datta Able PRO](datta-able-pro.md) - premium Bootstrap dashboard 
* [Jinja Material Dashboard](material-dashboard.md) - design crafted by Creative-Tim
* [Jinja Paper Dashboard](paper-dashboard.md) - lightweight Bootstrap design
* [Jinja Dashkit](dashkit-v3.md) \(legacy version\) - premium dashboard styled with Bulma
* [Jinja Volt Bootstrap 5](volt-bootstrap-5.md) - a nice dashboard template designed by [Themesberg](../../content/partners/themesberg.md)
* [Jinja Volt Dashboard PRO](volt-dashboard-pro.md) - premium dashboard template 

**Jinja** is basically an engine used to generate HTML or XML returned to the user via an HTTP response. For those who have not been exposed to a templating language before, such languages essentially contain variables as well as some programming logic, which when evaluated \(or rendered into HTML\) are replaced with actual values.

![Jinja - Official Logo.](../../.gitbook/assets/jinja-banner.jpg)

Jinja Templates provided by AppSeed are basically super simple Flask projects without database, ORM or other hard dependencies. We provide this kind of products for two reasons:

* **Jinja** can be used by many Python-based frameworks: Flask, Django, Bottle .. etc.
* **Jinja** is quite similar to other popular engines like Ejs, Liquid. 

On top of this, **Jinja** is the intermediate format used by AppSeed to convert the UI Kits to other engines and frameworks.    



### Why do we need Jinja?

**Sandboxed Execution** - It provides a protected framework for automation of testing programs, whose behavior is unknown and must be investigated.

**HTML Escaping** - Jinja has a powerful automatic HTML Escaping, which helps to prevent Cross-site Scripting \(XSS Attack\). There are special characters like &gt;,&lt;,&, etc. which carry special meanings in the templates. So, if you want to use them as regular text in your documents then, replace them with entities. Not doing so might lead to XSS-Attack.

**Template Inheritance** - This feature helps us to generate new pages starting from a base template that we inherit a common structure.



### Jinja Environment <a id="jinja-environment"></a>

Being a Python library, Jinja requires Python to run and expose the features. If you're not sure if Python is installed, just open a terminal and type `python --version`. The output should be something like this:

```text
$ python --version
Python 3.7.2 # <--- All good
```



> **Install Jinja** - using PIP \(python package manager\)

```text
$ pip install jinja2
```



> **Jinja in action -** a minimal code chunk

```python
>>> from jinja2 import Template
>>> t = Template("Hello {{ token }}!")
>>> t.render(token="Jinja2")
u'Hello Jinja2!'
```

The engine will replace the inner `token` with the value Jinja2. This is quite useful when we use this block for different token values.

