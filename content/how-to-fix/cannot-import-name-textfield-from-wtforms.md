---
description: >-
  This page explains How to Fix ImportError: cannot import name 'TextField' from
  'wtforms'
---

# Cannot import name 'TextField' from 'wtforms'

[WTForms](https://pypi.org/project/WTForms/) is a flexible forms validation and rendering library for Python web development. It can work with whatever web framework and template engine you choose. It supports data validation, CSRF protection, internationalization (I18N).&#x20;

![WTForms TextField import Error](../../.gitbook/assets/how-to-fix-cannot-import-name-textfield-from-wtforms.jpg)

### Error Text

```python
from wtforms import TextField
>> ImportError: cannot import name 'TextField' from 'wtforms'
```

The above error occurs when the `TextField` property is used with [WTForms](https://pypi.org/project/WTForms/) version 3.0 or above because the `wtforms.TextField` deprecated in favor of `wtforms.StringField`.

### How to Fix

> Solution 1 - Replace `TextField` type with `StringField`&#x20;

Note: This solution works with WTForms 3.x and 2.x versions

```python
from wtforms import StringField
// replace all TextField usages with StringField type 
```

> Solution 2 - Use the latest stable 2.x version of WTForms

```
// Use 2.x version
pip install WTForms==2.3.3
```

Using an older version provides a quick fix for your codebase but is not recommended in the long run.&#x20;


### Resources

* [WTForms](https://wtforms.readthedocs.io/en/3.0.x/) - official documentation
* [Flask](https://flask.palletsprojects.com/en/2.0.x/) - library documentation
* Join the [AppSeed](https://appseed.us/) community on [Discord](https://discord.gg/fZC6hup).
