---
description: Short introduction to Panini
---

# What is [Panini](https://github.com/foundation/panini)
---

A super simple flat file generator for use with Gulp. It compiles a series of HTML pages using a common layout. These pages can also include HTML partials, external Handlebars helpers, or external data as JSON or YAML.

Panini isn't a full-fledged static site generator—rather, it solves the very specific problem of assembling flat files from common elements, using a templating language.

<br />

## [Panini](https://github.com/foundation/panini)
---

```bash
$ npm install panini --save-dev
```

<br />

## Panini Features
---

Panini loads layouts, partials, helpers, and data files once on first run. Whenever these files change, call panini.refresh() to get it up to date. You can easily do this inside a call to gulp.watch():

```bash
$ gulp.watch(['./src/{layouts,partials,helpers,data}/**/*'], [panini.refresh]);
```

<br />

### Partials
---

Path to a folder containing HTML partials. Partial files can have the extension .html, .hbs, or .handlebars. Each will be registered as a Handlebars partial which can be accessed using the name of the file.

```html
<!-- Renders partials/header.html -->
{{> header}}
```

<br />

### Helpers
---

Path to a folder containing Handlebars helpers. Handlebars helpers are .js files which export a function via module.exports. The name used to register the helper is the same as the name of the file.

For example, a file named markdown.js that exports this function would add a Handlebars helper called {{markdown}}.

```javascript
var marked = require('marked');

module.exports = function(text) {
  return marked(text);
}
```

<br />

## Panini SSG Starters
---

- [JAMStack Paper Kit](https://appseed.us/apps/jamstack/jamstack-paper-kit)
- [JAMStack Now UI Kit](https://appseed.us/apps/jamstack/jamstack-now-ui-kit)
- [JAMStack Material Kit](https://appseed.us/apps/jamstack/jamstack-material-kit)

![Paper Kit - Built with Panini SSG](https://raw.githubusercontent.com/app-generator/static/master/products/jamstack-paper-kit-intro.gif)

<br />

## Resources
---

- [Panini](https://github.com/foundation/panini) - the source code (Github)
- [Panini Websites](https://appseed.us/apps/jamstack) - website built with Panini
