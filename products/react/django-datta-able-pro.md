---
description: >-
  Premium seed project built in React and Django on top of Datta Able Dashboard
  (PRO version)
---

# Django React Datta PRO

Open-source full-stack seed project coded in [**React** and **Django**](https://appseed.us/product/django-react-datta-able) on top of a modern design from **CodedThemes**. The **React** / **Django** codebase is already configured with an SQLite database, API, and JWT token-based authentication flow.

* [Django React Datta PRO](https://appseed.us/product/django-react-datta-able-pro) - product page
* [Django React Datta PRO](https://django-react-datta-able-pro.appseed-srv1.com/) - LIVE demo

![Django React - datta Able PRO.](../../.gitbook/assets/django-react-datta-pro-xs.jpg)

### Product features

The product expects a running API backend that exposes an interface for login/logout and register actions. By default, the guest users are redirected to the login page. Once the user is authenticated using an existing account or the new one, all private pages are accessible. Here are the steps to compile the product. 

> Dependencies

To use the product, **Python3** is required, and **GIT** command-line tool to clone/download the project from the public repository.

> **Step \#1** - Clone the project

```bash
$ git clone https://github.com/app-generator/priv-react-datta-able-dashboard-pro.git
$ cd priv-react-datta-able-dashboard-pro
```

> **Step \#2** - Install dependencies via NPM or yarn

```bash
$ npm i
// OR
$ yarn 
```

> **Step \#3** - Start in development mode

```bash
$ npm run start 
// OR
$ yarn start 
```

> **Step \#4** - Configure the backend - `src/config.js`

```javascript
const config = {
    ...
    API_SERVER: 'http://localhost:5000/api/'  // <-- The magic line
}; 
```

### 

### Django API Server

To use the product and see all features in action an API server should be up and running. This can be done in two ways:

* Compile and start a simple [**Django API Server**](../../boilerplate-code/api-server/django.md) already built to work with this frontend
* Mock a test server using the [**API Interface**](../../boilerplate-code/api-server/api-unified-definition.md) definition.

![Django API Server - Open-source product.](../../.gitbook/assets/api-cover-django-xs.jpg)

Here we will use the first option and build a real API server coded in **Django Framework** on top of [DRF](https://www.django-rest-framework.org/) Library with SQLite persistence.

> **Step \#1** - Clone the API Server from Github

```text
$ git clone https://github.com/app-generator/api-server-django.git
$ cd api-server-django 
```

> **Step \#2** - Install dependencies

```text
$ virtualenv -p python3 venv
$ source venv/bin/activate 
$
$ pip install -r requirements.txt
```

> **Step \#3** - Start the APi Server

```text
$ python manage.py migrate
$ python manage.py runserver 5000 
```

The API server will start using the default port `5000`.

With backend and frontend up & running, we can start using the product, register. and authenticate. The React UI will reveal the private pages once the users are authenticated. 

![Django React Datta PRO - Login Page.](../../.gitbook/assets/django-react-datta-pro-login-xs.jpg)

