---
description: >-
  Premium seed project built in React and Node JS on top of Datta Able Dashboard
  (PRO version)
---

# React Node JS Datta PRO

Full-stack seed project coded in **React** and **Node JS** on top of a modern design from CodedThemes\*\*: React Datta Abe PRO\*\*. The React / NodeJS codebase is already configured with a Mongo database, API, and authentication flow.

* [React Node JS Datta PRO](https://appseed.us/product/react-node-js-datta-able-pro) - product page
* [React Node JS Datta PRO](https://react-node-js-datta-able-pro.appseed-srv1.com/) - LIVE demo

![React Node JS - Datta Able PRO.](<../../.gitbook/assets/react-firebase-datta-able-pro-screen-xs (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2).jpg>)

## Product features

The product expects a running API backend that exposes an interface for login/logout and register actions. By default, the guest users are redirected to the login page. Once the user is authenticated using an existing account or the new one, all private pages are accessible. Here are the steps to compile the product.

> Dependencies

To use the product, a decent version of **Node JS** (>= 12.x) is required, and **GIT** command-line tool to clone/download the project from the public repository.

> **Step #1** - Clone the project (private repository)

```bash
$ git clone https://github.com/app-generator/priv-react-datta-able-dashboard-pro.git
$ cd priv-react-datta-able-dashboard-pro
```

> **Step #2** - Install dependencies via NPM or yarn

```bash
$ npm i
// OR
$ yarn 
```

> **Step #3** - Start in development mode

```bash
$ npm run start 
// OR
$ yarn start 
```

> **Step #4** - Configure the backend - `src/config/constant.js`

```javascript
const config = {
    ...
    API_SERVER: 'http://localhost:5000/api/'  // <-- The magic line
}; 
```

## API Server

To use the product and see all features in action an API server should be up and running. This can be done in two ways:

* Compile and start a simple [Node JS API](https://github.com/app-generator/api-server-nodejs) already built to work with this frontend
* Mock a test server using the [API Interface](https://github.com/app-generator/api-server-nodejs/blob/master/media/api.postman\_collection.json) definition

Here we will use the first version and build a real API server coded in Node JS/Express and MongoDB.

> API Server Description

Express / Nodejs Starter with JWT authentication, MongoDB where authentication is based on [json web tokens](https://jwt.io/). `passport-jwt` strategy is used to handle the Email/Password authentication. After a successful login, the generated token is sent to the requester.

> Dependencies

* [Node.js](https://nodejs.org/) >= 12.x
* [MongoDB](https://www.mongodb.com/) server

> **Step #1** - Clone the API Server from Github

```bash
$ git clone https://github.com/app-generator/api-server-nodejs.git
$ cd api-server-nodejs 
```

> **Step #2** - Install dependencies via NPM or yarn

```bash
$ npm i
// OR
$ yarn 
```

> **Step #3** - Start in development mode

```bash
$ npm dev
// OR
$ yarn dev 
```

The API server will start using the `PORT` specified in `.env` file, default value `5000` , same as the one expected by the front end.

From this point, the React Product should be able to authenticate and register new users.

![React Node JS Datta PRO - Login Page.](../../.gitbook/assets/react-node-js-datta-able-pro-login-xs.jpg)

## Resources

* [React Node JS Datta Able](https://appseed.us/product/react-node-js-datta-able) - the open-source version
* Free [Support](https://appseed.us/support) via eMail and **Discord** (for registered users)
