---
description: Add a simple JWT authentication to a React Template
---

# How to Implement JWT Authentication in React

This page explains how to update a React Template to support authentication using the JWT strategy. After the update, the project will have the following features:&#x20;

* Guest users are redirected to authenticate
* Users are able to authenticate using a registered account
* Users are able to register new accounts
* Users are able to logout from the application
* The App will use an open-source [Node JS Backend](https://github.com/app-generator/api-server-nodejs) published on Github - Product features:
  * [API Definition](https://docs.appseed.us/boilerplate-code/api-unified-definition) - the unified API structure implemented by this server
  * Simple, intuitive codebase - can be extended with ease.
  * TypeScript, Joy for validation
  * **Stack**: NodeJS / Express / SQLite / TypeORM
  * Auth: Passport / `passport-jwt` strategy



### Used Template: Soft UI React

Soft UI Dashboard is an open-source React Dashboard template crafted by Creative-Tim on top of M-UI (ex. Material-UI), the most popular components library for React. The product can be downloaded from the official product page but also directly from Github and compiled in a local environment:&#x20;

```bash
$ git clone https://github.com/creativetimofficial/soft-ui-dashboard-react.git
$ cd soft-ui-dashboard-react
$
$ yarn       # install dependencies
$ 
$ yarn start # start for development 
$
$ yarn build # production build 
```

In order to make this template a real app enhanced with a usable JWT authentication flow, we will make a few changes over the codebase:

* \#1 - Update Dependencies
  * Add formik
* \#2 - Code the Guard component
* \#3 - Define  the app `store` to handle the persistence on the client-side&#x20;
* @Todo
* @Todo



### 1# - Update Dependencies

@ToDo

### 2# - Code Auth Guard Component

@Todo

