---
description: >-
  Open-source Node JS API Server enhanced with JWT Authentication and SQLite
  storage.
---

# API Server Node JS

Free API Server coded on top of Express / Node JS with **SQLite** persistence and JWT authentication via Passport library - `passport-jwt` strategy.

> Product Links

* [API Definition](api-unified-definition.md) - the unified API structure implemented by this server
* [Node JS API Server](https://github.com/app-generator/api-server-nodejs) - source code
* Full-stack samples compatible with this product:
  * [React Berry Dashboard](https://github.com/app-generator/react-berry-admin-template) - open-source sample
  * [React Datta Dashboard](https://github.com/app-generator/react-datta-able-dashboard) - open-source sample

> API Methods - for full description please access [API Unified Definition](api-unified-definition.md)

* USERS API:
  * `/api/users/register`: create a new user
  * `/api/users/login`: authenticate an existing user
  * `/api/users/logout`: delete the associated JWT token
  * `/api/users/checkSession`: check an existing JWT Token for validity
  * `/api/users/edit` - edit the information associated with a registered user

![Node JS API Server - Open-source Product.](../../.gitbook/assets/api-cover-nodejs-xs.jpg)


## Requirements

* [Node.js](https://nodejs.org) >= 12.x
* [SQLite](https://www.sqlite.org/index.html)


## How to use the code

>**Step #1 -** Clone the sources

```
$ git clone https://github.com/app-generator/api-server-nodejs.git
$ cd api-server-nodejs
```

**Install dependencies** via NPM or Yarn

```
$ npm i
// OR
$ yarn
```

**Run the SQLite migration**

```
$ yarn typeorm migration:run
```

**Start the API server** - development mode

```
$ npm dev
// OR
$ yarn dev
```

**Production Build** - files generated in `build` directory

```
$ npm build
// OR
$ yarn build
```

**Start the API server** - for production (files served from `build/index.js`)

```
$ npm start
// OR
$ yarn start
```

The API server will start using the `PORT` specified in `.env` file (default 5000)\


## Codebase Structure

```
< ROOT / src >
     | 
     |-- config/                              
     |    |-- config.ts             # Configuration       
     |    |-- passport.ts           # Define Passport Strategy             
     | 
     |-- migration/
     |    |-- some_migration.ts     # database migrations
     |
     |-- models/                              
     |    |-- activeSession.ts      # Sessions Model (Typeorm)              
     |    |-- user.ts               # User Model (Typeorm) 
     | 
     |-- routes/                              
     |    |-- users.ts              # Define Users API Routes
     | 
     | 
     |-- index.js                     # API Entry Point
     |-- .env                       # Specify the ENV variables
     |                        
     |-- ************************************************************************
```

### SQLite Path

The SQLite Path is set in `.env`, as `SQLITE_PATH`

### Database migration

> Generate migration:

```
$ yarn typeorm migration:generate -n your_migration_name
```

> run migration:

```
$ yarn typeorm migration:run
```


## Compatible Fullstack Products

The product can be used as a standalone server but also as an authentication server for React, Vue products. Such a product already configured with Django API Server is [**React Datta Able**](https://appseed.us/product/react-node-js-datta-able)**,** an open-source React Dashboard.

* ​[React Datta Able](https://appseed.us/product/react-node-js-datta-able) - product page
* ​[React Datta Able](https://github.com/app-generator/react-datta-able-dashboard) - source code

![React Datta Able - Open-Source Dashboard.](https://gblobscdn.gitbook.com/assets%2F-MYVW6MKCi9iujNc3SK\_%2F-Memyr3wdOIsonokJPUQ%2F-Men-RiulajMsyVGTEgy%2Freact-datta-able-cover.jpg?alt=media\&token=c87fbe5e-44b0-4d3d-9bb3-c41495fbb567)
