---
description: Short introduction to Multi-Tier Architecture
---

# N-Tier Architecture

Multi-tier architecture \(often referred to as n-tier architecture\) or multilayered architecture is a client–server architecture in which presentation, application processing, and data management functions are physically separated. Using a N-tier architecture, web developers can create modular applications.

## Common layers

In a multilayered architecture the most common used layers are:

* Presentation layer - the visual part of an web application
* Application layer - the server-side of an web application 
* Database layer - the persistance layer where information is saved and updated 

### Presentation layer

This layer handles the user interaction. This part of the application is usually built in HTML and Javascript in various technologies and frameworks:

* [React](https://reactjs.org/) - the popular Javascript framework built by Facebook
* [Vue.js](https://vuejs.org/) - The Progressive JavaScript Framework
* [jQuery](https://jquery.com/)   

### Application layer

Represents the server side of the application and can be developed in many programming languages:

* [Php](https://www.php.net/) \(the most popular server-side language \) using [Laravel](https://laravel.com/), [CodeIgniter](https://www.codeigniter.com/)
* [Python](https://www.python.org/) server-side apps can be developed using [Django](https://www.djangoproject.com/), [Flask](http://flask.pocoo.org/)
* [Ruby](https://www.ruby-lang.org/en/)

### Database layer

The majority of web apps requires a type of storage to save the relevant data:

* [MySql](https://www.mysql.com/) - the popular open-source database engine 
* [SQLite](https://www.sqlite.org/index.html) - the lite version of mysql
* [MongoDB](https://www.mongodb.com/)

## Common Architectures

In web development the most used architectures are:

### [Single Tier architecture](https://github.com/app-generator/docs/tree/a7c2441bf81cb9d2ad47b81b25204d5fc21897d9/what-is/single-tier-architecture/README.md)

The web application is served only once by the server, and runs entirely on the client side - read [more](https://github.com/app-generator/docs/tree/a7c2441bf81cb9d2ad47b81b25204d5fc21897d9/what-is/single-tier-architecture/README.md)

![Single Tier architecture](https://raw.githubusercontent.com/app-generator/static/master/docs/single-tier-architecture-sm.jpg)

### [Two Tier architecture](https://github.com/app-generator/docs/tree/a7c2441bf81cb9d2ad47b81b25204d5fc21897d9/what-is/two-tier-architecture/README.md)

Sometimes named Full-Stack architecture - read [more](https://github.com/app-generator/docs/tree/a7c2441bf81cb9d2ad47b81b25204d5fc21897d9/what-is/two-tier-architecture/README.md)

![Two Tier architecture](https://raw.githubusercontent.com/app-generator/static/master/docs/two-tier-architecture-sm.jpg)

## Related Resources

* Wikipedia [Multitier Architecture](https://en.wikipedia.org/wiki/Multitier_architecture)
* [N Tier Architecture](https://www.guru99.com/n-tier-architecture-system-concepts-tips.html) with example
* Techopedia [One-Tier Architecture](https://www.techopedia.com/definition/17374/one-tier-architecture) 
* Techopedia [Two-Tier Architecture](https://www.techopedia.com/definition/467/two-tier-architecture) 
* [Single-Tier vs. Multi-Tier Architecture](https://docs.bitnami.com/google-templates/singletier-vs-multitier/) 

