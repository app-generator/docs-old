---
description: Open-source Django API server that explains how to extend an existing codebase
---

# Django API Server

This sample explains how to extend an existing Django API Starter and add another model managed via a new API node.

* [Django API Server](../../boilerplate-code/api-server/django.md) - original project
* [Django API Server Sample](https://github.com/app-generator/api-server-django-sample) - the source code with new enhancements


## Codebase structure

```
PROJECT ROOT
├── api                           # App containing all project-specific apps
│   ├── apps.py
│   ├── authentication            # Implements authentication app logic (register, login, session) logic
│   │   ├── apps.py
│   │   ├── backends.py           # Handles the active session authentication
│   │   ├── migrations
│   │   ├── serializers
│   │   │   ├── login.py          # Handles the proccess of login for an user
│   │   │   └── register.py       # Handle the creation of a new user
│   │   ├── tests.py              # Test for login, registration and session
│   │   └── viewsets       
│   │       ├── active_session.py # Handles session check
│   │       ├── login.py          # Handles login
│   │       ├── logout.py         # Handles logout
│   │       └── register.py       # Handles registration
|   |
│   ├── fixtures                  # Package containg the project fixtures
│   ├── __init__.py
│   ├── routers.py                # Define api routes
│   └── user                      # Implements user app logic
│       ├── apps.py
│       ├── __init__.py
│       ├── migrations
│       ├── serializers.py       # Handle the serialization of user object
│       └── viewsets.py          # Handles  the modification of an user
|
├── core                         # Implements app logic      
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py              # Django app bootstrapper
│   ├── test_runner.py           # Custom  test runner
│   ├── urls.py    
│   └── wsgi.py
|
├── docker-compose.yml
├── Dockerfile
├── .env                         # Inject Configuration via Environment
├── manage.py                    # Starts the app
└── requirements.txt             # Contains development packages
```


## Used Patterns

Working with Django Rest Framework, the most common design pattern is the **Template Method Pattern**.

It mostly consists of providing base/skeleton for some features with the possibility to override/extends these skeletons.

For example, you can check the code in `api/user/viewsets.py`. The `UserViewSet` inherits of `viewsets.GenericsViewSet` and `CreateModelMixin` and `UpdateModelMixin`.

The `UpdateModelMixin` provides the logic to update an object using `PUT`.

We only need to rewrite the method which handles the `updating` and provides the `serializer_class` and the `permission_classes`.


## How to use the API

> POSTMAN usage

The API is actually built around these endpoints :

* `api/users/signup`
* `api/users/login`
* `api/users/edit`
* `api/users/checkSession`
* `api/users/logout`

> **Register** - `api/users/register`

```javascript
POST api/users/register
Content-Type: application/json

{
    "username":"test",
    "password":"pass", 
    "email":"test@appseed.us"
}
```

**Response :**

```javascript
{
    "success": true,
    "userID": 1,
    "msg": "The user was successfully registered"
}
```

> **Login** - `api/users/login`

```
cd api && django-admin startapp transactions
```

Once it's done, rewrite the `apps.py` file with the following content.

```
```

```javascript
POST /api/users/login
Content-Type: application/json

{
    "password":"pass", 
    "email":"test@appseed.us"
}
```

**Response :**

```javascript
{
    "success": true,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNjI4NzgxNTY4fQ.mB_YcZxZJd37r_4NYnLYeCByEHKGBC2ob0xe9KgcOII",
    "user": {
        "_id": 1,
        "username": "test",
        "email": "test@appseed.us"
    }
}
```

> **Logout** - `api/users/logout`

```javascript
POST api/users/logout
Content-Type: application/json
authorization: JWT_TOKEN (returned by Login request)

{
    "token":"JWT_TOKEN"
}
```

**Response :**

```javascript
{
    "success": true,
    "msg": "Token revoked"
}
```

> cURL usage

Let's edit information about the user and check a session using cURL.

> **Check Session**- `api/users/checkSession`

```
curl --request POST \
  --url http://127.0.0.1:8000/api/users/checkSession \
  --header 'Authorization: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNjI4NzgxNTY4fQ.mB_YcZxZJd37r_4NYnLYeCByEHKGBC2ob0xe9KgcOII' \
  --header 'Content-Type: application/json'
```

**Response :**

```javascript
{
  "success": true
}
```

> **Edit User** - `api/users/edit`

```
curl --request POST \
  --url http://127.0.0.1:8000/api/users/edit \
  --header 'Authorization: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNjI4NzgxNTY4fQ.mB_YcZxZJd37r_4NYnLYeCByEHKGBC2ob0xe9KgcOII' \
  --header 'Content-Type: application/json' \
  --data '{
	"username": "tester",
	"email": "test@admin.us",
	"userID": 1
}'
```

**Response :**

```javascript
{
  "success": true
}
```


## How to extend API

> Add a new model - transactions

To add a model for `transaction` in the project, let's create a new application in the `api` directory.

* Creating the app using `django-admin` command in the `api` directory.
* Then modify the name and the label of the app in `apps.py`
* And add the `app` in the `INSTALLED_APPS` in the `settings.py` of the project.

```
cd api && django-admin startapp transaction
```

Then modify the `apps.py` file.

```python
# api/transaction/apps.py

from django.apps import AppConfig


class TransactionConfig(AppConfig):
    default_auto_field = 'django.db.models.BigAutoField'
    name = 'api.transaction'
    label = 'api_transaction'
```

And don't forget to add the `default_app_config` in the `__init__.py` file the `transaction` directory.

```python
# api/transaction/__init__.py

default_app_config = "api.transaction.apps.TransactionConfig"
```

We can now register the application in `settings.py` file.

```python
# core/settings.py

INSTALLED_APPS = [
    ...
    "api.authentication",
    "api.transaction"
]
```

> Add API interface to manage transactions

Creating an API interface to manage transactions usually go this way :

* Creating the model
* Creating the serializer
* Write the views or the viewsets
* Register the viewsets by creating routes

We've already created the model for `transaction`.

Let's create the [serializer](https://www.django-rest-framework.org/api-guide/serializers/). 

A [serializer](https://www.django-rest-framework.org/api-guide/serializers/) allows us to convert complex Django complex data structures such as `querysets` or model instances in Python native objects that can be easily converted JSON/XML format, but a serializer also serializes JSON/XML to naive Python.

```python
# api/transaction/serializers.py

from api.transaction.models import Transaction
from rest_framework import serializers


class TransactionSerializer(serializers.ModelSerializer):
    info = serializers.CharField(allow_null=True, allow_blank=True)
    price = serializers.IntegerField(required=True)

    class Meta:
        model = Transaction
        fields = ["id", "product", "price", "qty", "discount", "info"]
        read_only_field = ["id", "created"]
```

And now the [viewsets](https://www.django-rest-framework.org/api-guide/viewsets/).

The routes for the transaction interface API should look like this :

* `api/transactions/create` -> create transaction
* `api/transactions/edit/id`-> edit transaction
* `api/transactions/delete/id` -> delete transaction
* `api/transactions/get/id` -> get specific transaction
* `api/transactions/get` -> get all transactions

The [ViewSet](https://www.django-rest-framework.org/api-guide/viewsets/#viewset) class comes with built-in [actions](https://www.django-rest-framework.org/api-guide/viewsets/#viewset-actions) :

* list
* retrieve
* create
* update
* partial\_update
* destroy

And to make sure the names of the URLs match what we need, we'll be using [actions](https://www.django-rest-framework.org/api-guide/viewsets/#marking-extra-actions-for-routing).

First of all, create a file name `viewsets` in the `transactions` directory.

And add the following code.

```python
# api/transactions/viewsets.py

from rest_framework import viewsets, status
from rest_framework.response import Response
from rest_framework.exceptions import ValidationError, NotFound, MethodNotAllowed
from rest_framework.decorators import action
from rest_framework.permissions import IsAuthenticated

from django.core.exceptions import ObjectDoesNotExist

from api.transaction.models import Transaction
from api.transaction.serializers import TransactionSerializer


class TransactionViewSet(viewsets.ModelViewSet):
    serializer_class = TransactionSerializer
    permission_classes = (IsAuthenticated,)
    http_method_names = ['get', 'post']
    
    not_found_message = {"success": False, "msg": "This object doesn't exist."}
    missing_id_message = {"success": False, "msg": "Provide a transaction id."}
```

Then let's rewrite the `get_queryset` method. This method is used by the viewset to return a list of objects, here a list of transactions.

```python
class TransactionViewSet(viewsets.ModelViewSet):
    ...

    def get_queryset(self):
        return Transaction.objects.all()
```

Great. Now, let's make sure DRF will exactly match the URLs we want. First of all, we have to block the default routes.

```python
class TransactionViewSet(viewsets.ModelViewSet):
    ...

    def list(self, request, *args, **kwargs):
        raise MethodNotAllowed('GET')

    def create(self, request, *args, **kwargs):
        raise MethodNotAllowed('POST')

    def destroy(self, request, *args, **kwargs):
        raise MethodNotAllowed('DELETE')

    def update(self, request, *args, **kwargs):
        raise MethodNotAllowed('PUT')

    def retrieve(self, request, *args, **kwargs):
        raise MethodNotAllowed('GET')
```

And we can write our own actions now.

Let's start with `api/transactions/create`.

```python
class TransactionViewSet(viewsets.ModelViewSet):
    ...

    @action(methods=['post'], detail=False, url_path='create')
    def create_transaction(self, request, *args, **kwargs):
        data = request.data

        serializer = self.serializer_class(data=data)
        serializer.is_valid(raise_exception=True)
        serializer.save()

        return Response({
            "success": True
        }, status.HTTP_201_CREATED)
```

To avoid name collision with the default built-in method `create` , we are naming the method `create_transaction`. Hopefully, DRF provides the option to specify the `url_path` of the method.

Let's write the actions for `api/transactions/get` and `api/transactions/get/id`

```python
class TransactionViewSet(viewsets.ModelViewSet):
    ...
    
    @action(methods=['get'], detail=False, url_path='get')
    def get_transactions(self, request, *args, **kwargs):

        transactions = self.get_queryset()

        page = self.paginate_queryset(transactions)

        if page is not None:
            serializer = self.get_serializer(page, many=True, context=self.get_serializer_context())
            return self.get_paginated_response(serializer.data)

        serializer = self.get_serializer(transactions, many=True, context=self.get_serializer_context())
        return Response({
            "success": True,
            "transactions": serializer.data
        }, status=status.HTTP_200_OK)

    @action(methods=['get'], detail=False, url_path=r'get/(?P<transaction_id>\w+)')
    
    def get_transaction(self, request, transaction_id=None, *args, **kwargs):

        if transaction_id is None:
            raise ValidationError(self.missing_id_message)

        try:
            obj = Transaction.objects.get(pk=transaction_id)
        except ObjectDoesNotExist:
            raise NotFound(self.not_found_message)

        serializer = self.get_serializer(obj)

        return Response({
            "success": True,
            "transaction": serializer.data
        }, status=status.HTTP_200_OK)
```

Notice that for the  `get/id` (`get_transaction`), we are writing the `url_path` using **regex expression**.

And finally, the actions for `api/transactions/delete/id` and `api/transactions/edit`.

```python
class TransactionViewSet(viewsets.ModelViewSet):
    ...
    @action(methods=['post'], detail=False, url_path=r'edit/(?P<transaction_id>\w+)')
    def edit_transaction(self, request, transaction_id=None, *args, **kwargs):

        if transaction_id is None:
            raise ValidationError(self.missing_id_message)

        try:
            obj = Transaction.objects.get(pk=transaction_id)
        except ObjectDoesNotExist:
            raise NotFound(self.not_found_message)

        serializer = self.get_serializer(obj, data=request.data, partial=True)
        serializer.is_valid(raise_exception=True)
        self.perform_update(serializer)

        if getattr(obj, "_prefetched_objects_cache", None):
            obj._prefetched_objects_cache = {}

        return Response({
            "success": True
        }, status.HTTP_200_OK)

    @action(methods=['post'], detail=False, url_path=r'delete/(?P<transaction_id>\w+)')
    def delete_transaction(self, request, transaction_id=None, *args, **kwargs):

        if transaction_id is None:
            raise ValidationError(self.missing_id_message)

        try:
            obj = Transaction.objects.get(pk=transaction_id)
        except ObjectDoesNotExist:
            raise NotFound(self.not_found_message)

        obj.delete()

        return Response({
            "success": True
        }, status.HTTP_200_OK)
```

Now, we can register the viewset.

There is already a `routers.py` file which contains the routes for `api/users`.

Let's create a different [router](https://www.django-rest-framework.org/api-guide/routers/) for transactions.

In the `api` directory, create a new package called `routers`. Move the file `routers.py` in it and rename it to `users.py`.

Then create a new file named `transactions.py` and add the following code to register `TransactionViewSet` actions.

```python
# api/routers/transactions.py

from rest_framework import routers

from api.transaction.viewsets import TransactionViewSet

router = routers.SimpleRouter(trailing_slash=False)

router.register('', TransactionViewSet, basename='transactions')

urlpatterns = [
    *router.urls,
]
```

And the last step, open the urls.py file in the core directory and add the transaction router.

```python
# core/urls.py

from django.urls import path, include

urlpatterns = [
    path("api/users/", include(("api.routers.users", "api-users"), namespace="api-users")),
    path("api/transactions/", include(("api.routers.transactions", "api-transactions"), namespace="api-transactions"))
]
```

And that's it. You can start testing the API with Postman.

Congratulations. You just learned :

* How to add a new model;
* How to add a serializer for this model;
* How to rewrite `viewset` behavior and `actions` to match your needs.
