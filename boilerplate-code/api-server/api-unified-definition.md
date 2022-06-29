---
description: >-
  The common definition used in all AppSeed products that includes an API
  Service
---

# API Unified Definition

This page describes the **unified definition** used by all API servers provided by AppSeed. This internal standard is used by all full-stack products, despite the UI or backend technology.

> API Servers aligned to use it:

* [API Server Django](django.md) - free product
* [API Server Flask](flask.md) - free product
* [API Server Node JS](node-js.md) - free product
* [API Server Node JS PRO](https://github.com/app-generator/api-server-nodejs-pro) - commercial product

> UI Products aligned to use it:

* [React Berry Dashboard](https://appseed.us/product/berry-dashboard/api-server-nodejs/react/) - free product
* [React Datta Able](https://appseed.us/product/datta-able/api-server-nodejs/react/) - free product
* [React Datta Able PRO](https://appseed.us/product/datta-able-pro/full-stack/react/) - commercial product

> For more information or support please access the [AppSeed](https://appseed.us) platform or chat directly with support team on [Discord](https://appseed.us/support).

## ✨ API Information

> Interface descriptor - [POSTMAN collection format](https://github.com/app-generator/api-unified-definition/blob/main/api.postman\_collection.json)

* USERS API:
  * `/api/users/register`: create a new user
  * `/api/users/login`: authenticate an existing user
  * `/api/users/logout`: delete the associated JWT token
  * `/api/users/checkSession`: check an existing JWT Token for validity
  * `/api/users/edit` - edit the information associated with a registered user

## ✨ API Samples

> 👉 **Register** - `api/users/register`

```
POST api/users/register
Content-Type: application/json

{
    "username":"test",
    "password":"pass", 
    "email":"test@appseed.us"
}
```

> 👉 **Login** - `api/users/login`

```
POST /api/users/login
Content-Type: application/json

{
    "password":"pass", 
    "email":"test@appseed.us"
}
```

> 👉 **Logout** - `api/users/logout`

```
POST api/users/logout
Content-Type: application/json
authorization: JWT_TOKEN (returned by Login request)

{
    "token":"JWT_TOKEN"
}
```
