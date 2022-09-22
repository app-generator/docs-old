---
description: Short introduction to JAMstack
---

# What IS JAMStack

Modern web development architecture based on client-side JavaScript, reusable APIs, and prebuilt Markup

### JAMstack - Short Introduction

Apps built in Jamstack architecture met the following criteria:

* **JavaScript**, any dynamic programming during the request/response cycle is handled by JavaScript, running entirely on the client
* **APIs**, all server-side processes or database actions are abstracted into reusable APIs, accessed over HTTPS with JavaScript
* **Markup**, templated markup should be prebuilt at deploy time, usually using a site generator for content sites, or a build tool for web apps



### Why using a JAMstack app?

The major advantages met by the JAMstack pattern are:

* Apps are much faster because there is no more dynamic build of the pages
* Security - a static app with less API endpoints reduce allot the risk of being hacked
* Better developer experience - using a JAMstack app a developer needs only a simple editor and a console to create and deploy an app



### Sample JAMstack App

For instance, let's build a sample JAMstack app by getting the source code from [Github](https://github.com/search?q=jamstack+fractal). Let's pick up the first result, open the [README](https://github.com/app-generator/jamstack-fractal/blob/master/README.md) file and follow the intructions provided:

```
$ git clone https://github.com/app-generator/jamstack-fractal.git
$ cd jamstack-fractal

$ yarn # install modules
$ yarn start # start the app for development

$ yarn build # build for production
```

If all goes well, the app can be visited on `http://localhost:8000` As we can see, building an app in JAMstack architecture is quite an easy job.


### Related Resources

* [JAMstack](https://jamstack.org/) - the website
* [WTF is JAMstack](https://jamstack.wtf/) - an well-known resource fpr JAMstack developers
* [Apps built in JAMstack](https://appseed.us/apps/jamstack) - index provided by AppSeed
* Open-Source [JAMstack Apps](https://github.com/app-generator/jamstack) published on [Github](https://github.com/search?q=jamstack)
* [Landed](https://appseed.us/apps/jamstack/html5up-landed) a very popular open-source app designed by **Html5 Up** and coded in JAMstack architecture
