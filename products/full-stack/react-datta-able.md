---
description: >-
  Premium React Dashboard designed by CodedThemes, coded as a full-stack product
  by AppSeed
---

# Full-Stack React Datta Able

Full-stack version of **Datta Able PRO**, a premium design crafted by **CodedThemes** now usable with multiple API Backend Servers: **Node JS**, Flask, Django. The UI comes with pre-configured **JWT authentication** powered by a [Unified API Interface](../../boilerplate-code/api-server/api-unified-definition.md) that makes this product compatible with more than one backend: Node JS, Flask, Django (FASTapi coming soon). 

* [Full-stack React Datta Able](https://appseed.us/full-stack/react-datta-able) - product page
* [Full-stack React Datta Able](https://fullstack-react-datta-able.appseed-srv1.com/) - LIVE Demo

![React Datta Able - Full-stack Version](<../../.gitbook/assets/react-firebase-datta-able-pro-screen-xs (2) (1) (1) (1) (1) (1).jpg>)


## Product Dependencies

To successfully compile and use the product, please make sure your workstation has the right tools installed and accessible in the terminal window:

* [Node JS](https://nodejs.org/en/) 12.x version (or above) - used to build both parts (frontend & backend)
* [GIT](https://git-scm.com/) versioning command-line tool - used to clone the sources from Github
* A code editor: [VsCode](https://code.visualstudio.com/) or [Atom](https://atom.io/)
* Ability to work in the terminal window  


## Product Features

The product aims to help developers skip over the basics and start faster a new full-stack product already enhanced with authentication, a pixel-perfect UI powered by production-ready backends. The fact that makes this full-stack product unique is the **JSON-API** compliance over multiple servers:

* ****[Node JS API](../../boilerplate-code/api-server/node-js.md): Typescript, Flexible persistence (SQLite, Mongo), TypeORM, Validation
* [Django API](../../boilerplate-code/api-server/django.md): JWT Authentication over DRF, SQLite, Docker
* [Flask API](../../boilerplate-code/api-server/flask.md): powered by Flask-JWT-extended, SQL-Alchemy, Docker
* Coming soon APIs: **FASTapi**, **Laravel API**

By default, the UI redirects the guest users to the login page. Once the user is authenticated, all private pages are unlocked.

> Implemented JWT Authentication Flow: Login, Logout, Register.

![Full-Stack React Datta Able - Login. ](<../../.gitbook/assets/django-react-datta-able-login-xs (1) (1).jpg>)


## **How to use the product**

Full-stack React Material Dashboard is built using a two-tier architecture where the UI is decoupled from the backend API server and communicates using requests secured by **JWT tokens**. The recommended way to start using this full-stack product is to follow a simple setup:

* Step #1 - Build and start the backend server
* Step #2 - Build and start the UI
* Create a new user via the registration page
* Authenticate and access the private pages
* Add your magic on top of the existing codebase.


## Start the backend server

As mentioned before, the UI is configured to work with many backend servers that share a common API interface: [Django](../../boilerplate-code/api-server/django.md), [Node JS](../../boilerplate-code/api-server/node-js.md), [Flask](../../boilerplate-code/api-server/flask.md). Based on your license (free or commercial) the access is granted to the request API Server. On this page, we will compile and start the free version of Node JS API (open-source product).

> Start [Node JS API Server](../../boilerplate-code/api-server/node-js.md) - open-source version

**Step #1 -** Clone the sources

```
$ git clone https://github.com/app-generator/api-server-nodejs.git
$ cd api-server-nodejs
```

**Step #2 - Install dependencies** via NPM or Yarn

```
$ npm i
// OR
$ yarn
```

**Step #3 - Run the SQLite migration** and create the required tables

```
$ yarn typeorm migration:run
```

**Step #4 - Start the API server** - development mode

```
$ npm dev
// OR
$ yarn dev
```

The API interface used by the API is a simple JWT authentication layer that exposes the following methods:

* USERS API:
  * `/api/users/register`: create a new user
  * `/api/users/login`: authenticate an existing user
  * `/api/users/logout`: delete the associated JWT token
  * `/api/users/checkSession`: check an existing JWT Token for validity
  * `/api/users/edit` - edit the information associated with a registered user

At this point, the backend API should be & and running on address: `http://localhost:5000`  and we can move on with the setup and build the React UI.


## Start the React UI

The **React Material Dashboard** being a commercial product, a license is required before getting access to the source code. In case you don't have a license, please access the product page and purchase one.

**Step #1** - Clone the project

```
$ git clone https://github.com/app-generator/priv-react-datta-able-dashboard-pro.git
$ cd priv-react-datta-able-dashboard-pro 
```

**Step #2** - Install dependencies via NPM or yarn

```
$ npm i
// OR
$ yarn
```

**Step #3** - Start in development mode

```
$ npm run start 
// OR
$ yarn start
```


## Backend Integration

> The backend API server address is saved in `src/config.js`.

```
const config = {
    ...
    API_SERVER: 'http://localhost:5000/api/'  // <-- The magic line
}; 
```


## **React Datta Able** - UI

_Official Product Information_ **-** Datta Able React is the **most stylized** React **Admin Template**, around all other admin templates **in the market**. It comes with high feature-rich pages and components with **fully developer-**centric code.

![Full-Stack React Datta Able - Charts Page.](../../.gitbook/assets/django-react-datta-able-widgets-xs.jpg)
