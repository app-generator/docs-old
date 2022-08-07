---
description: Getting Started with Next JS
---

# Getting Started

**Next.js** is a React framework that provides features such as rich User Experience, great performance, and faster feature development.&#x20;

The main difference with React lies in the way they handle the UI refresh and rendering. Next.js is fast because of the static destinations, server-side rendering and the way it handles image optimization. This fact leads to one of the main advantages of Next.js over React is that Next.js allows you to develop SEO-friendly static websites.

### ✨ Starting a Next.js project

If you have NPM installed, you can start a new Next project with the following command:&#x20;

```
npx create-next-app you-app
```

`create-next-app` is a little bit similar to Create React App, but it's actually for Next.js projects. Once the project is created, you can run the project using the following command `yarn dev`. The project will be running at `http://localhost:3000`.

### ✨ Next.js project structure

The structure of a Next.js project is very simple and straightforward.&#x20;

```bash
├── next.config.js
├── package.json
├── pages
│   ├── api
│   │   └── hello.js
│   ├── _app.js
│   └── index.js
├── public
│   ├── favicon.ico
│   └── vercel.svg
├── README.md
├── styles
│   ├── globals.css
│   └── Home.module.css
└── yarn.lock
```

In a `Next.js` project, you can find:

* `next.config.js` file containing all configurations related to the Next.js project. It is used for running the `Next.js` server and for build phases.
* `pages` is a folder containing pages that **Next.js** will serve but it also serves a core feature of **Next.js** which is routing. In fact, each page is associated with a route based on the file name. In the current case, you can find the `hello.js` page at `/api/hello`.&#x20;
* `styles` is a folder that contains the styles used in the project.&#x20;

With the basics of a Next.js project understood, we can move now to a simple project we will build in the next pages.

### ✨ [Next.js Starters](https://www.admin-dashboards.com/next-js-themes-open-source/)

In case this framework makes you curious to start a new project on top, here is a list of free starters powered by Next.js&#x20;

* 👉 [Next JS Argon Dashboard](https://www.creative-tim.com/product/nextjs-argon-dashboard?AFFILIATE=128200) - Bootstrap 4, React and Reactstrap
* 👉 [Notus Next JS](https://www.creative-tim.com/product/notus-nextjs?AFFILIATE=128200) - open-source template styled with Tailwind
* 👉 [Xtreme Next Js Free Admin](https://www.wrappixel.com/templates/xtreme-next-js-free-admin-template/?ref=157) - provided by WrapPixel&#x20;
