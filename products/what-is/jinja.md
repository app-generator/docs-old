---
description: Modern Template engine used in frameworks like Flask and Bottle
---

# Jinja Templating Language

[Jinja](https://jinja.palletsprojects.com/en/2.11.x/) is a modern and designer-friendly templating language for Python, modeled after Django’s templates. It is fast, widely used, and secure with the optional sandboxed template execution environment. Jinja is basically an engine used to generate HTML or XML returned to the user via an HTTP response.

For those who have not been exposed to a templating language before, such languages essentially contain variables as well as some programming logic, which when evaluated \(or rendered into HTML\) are replaced with actual values.

### Why do we need [Jinja](https://jinja.palletsprojects.com/en/2.11.x/)? <a id="why-do-we-need-jinja"></a>

**Sandboxed Execution** - It provides a protected framework for automation of testing programs, whose behavior is unknown and must be investigated.

**HTML Escaping** - Jinja has a powerful automatic HTML Escaping, which helps to prevent Cross-site Scripting \(XSS Attack\). There are special characters like &gt;,&lt;,&, etc. which carry special meanings in the templates. So, if you want to use them as regular text in your documents then, replace them with entities. Not doing so might lead to XSS-Attack.

**Template Inheritance** - This feature helps us to generate new pages starting from a base template that we inherit a common structure.

