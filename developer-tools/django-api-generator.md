---
description: Developer Tool - Dynamic API Generator
---

# Django API Generator

The tool is able to `generate APIs` using **Django & DRF** stack with a minimum effort. For newcomers, **Django** is a leading backend framework used to code from simple websites and APIs to complex eCommerce solutions.

- 👉 [Django API Generator](https://github.com/app-generator/devtool-django-api-generator) - `Source code`
- 👉 Free [support](https://appseed.us/support/) via Email and `Discord`
- 👉 More [Developer Tools](https://appseed.us/developer-tools/) - provided by AppSeed


## Quick start in `Docker`

> 👉 **Step 1** - Download the code from the GH repository (using `GIT`) 

```bash
$ git clone https://github.com/app-generator/devtool-django-api-generator.git
$ cd devtool-django-api-generator
```

> 👉 **Step 2** - Start the APP in `Docker`

```bash
$ docker-compose up --build 
```

Visit `http://localhost:5085` in your browser. By default a simple [Books](./apps/models.py) Model is used as sample.  

- The generated DRF API is live at `http://localhost:5085/api/books`
- Registered users can interact with the API using the `API-View` page

![Django API Generator - API View page for Books Model.](https://user-images.githubusercontent.com/51070104/194476781-6476de62-191a-48e8-8730-344c2d63f9d0.png) 


## Video Presentation

{% embed url="https://www.youtube.com/watch?v=xREQr9GAsaY" %}
Django API Generator - Tools for Developers
{% endembed %}


## How It Works

> 👉 **Step #1** - Define models in `apps/models.py`

By default, the project comes with a simple `Books` model: 

```python
class Book(models.Model):

    name = models.CharField(max_length=100)
```

> 👉 **Step #2** -  `Register the model` in `core/settings.py` (API_GENERATOR section)

```python
API_GENERATOR = {
    'books': "Book", # <-- Books model provided as sample
}
```

> 👉 **Step #3** - `Migrate Database`

```bash
$ python manage.py makemigrations
$ python manage.py migrate
```

> 👉 **Step #4** - `Generate API` 

```bash
$ python manage.py generate-api
```

`Note`: if you define a model that wasn't migrated to db, you will see an error that say names of not migrated models and codes will not generate.

> 👉 **Step #5** - `Use the API` 

* Create a book by `POST` request to `/api/books/`
* Get book that has id = 2 by `GET` request to `/api/books/2/`
* Get all books by `GET` request to `/api/books/`
* Update book that has id = 2 by `PUT` request to `/api/books/2/`
* delete book that has id = 2 by `DELETE` request to `/api/books/2/`


## 🚀 Where to go from here

- 👉 Contact AppSeed using the [support](https://appseed.us/support/) page
- 👉 Use the [App Generator](https://appseed.us/generator) to generate a new project
