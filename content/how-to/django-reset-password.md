---
description: A simple way to code a reset password mechanism in Django
---

# Django Reset Password

This page explains how to implement a password reset mechanism in Django.&#x20;

Django comes with a password reset feature. You can extend these features to modify the default behavior.

For example, the `views` from `django.contrib.auth` comes with support for login, logout, and all the password reset flow.

&#x20;First of all, in the `urls.py`file, add the following routes.

```python
from django.contrib.auth import views

urlpatterns = [
    path('password_reset/', views.PasswordResetView.as_view(), name="password_reset"),
    path('reset/<uidb64>/<token>/', views.PasswordResetConfirmView.as_view(), name="password_reset_confirm"),
    path('password_reset/done/', views.PasswordResetDoneView.as_view(), name="password_reset_done"),
    path('reset/done/', views.PasswordResetCompleteView.as_view(), name="password_reset_complete"),
    path('activate/<uidb64>/<token>/', activate_account, name='activate')
]
```

&#x20;These routes and views use the default Django templates.&#x20;

But how do you use your own templates?

Well, Just create a directory named `registration` in your `TEMPLATE` directory.

When looking at the code of the `views.PasswordResetView` class, you can notice the name of the template used.

```python
class PasswordResetView(PasswordContextMixin, FormView):
    ...
    template_name = 'registration/password_reset_form.html'
    ...
```

Then inside the `registration` directory created recently, create a file named `password_reset_form.html`

