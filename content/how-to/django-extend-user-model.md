---
description: How to extend the default user model in Django with more fields
---
# Django Extend User Model

This page explains how to extend the default User Model in Django and associate with a user other information like address, phone number .. etc.

Django provides a User model you can use for authentication or authorization. 

But what if you need more fields? Such as address, phone number, city ...etc. In that case, you can just extend the user model, here the `AbstractUser` class.

```python
from django.db import models
from django.contrib.auth.models import AbstractUser 

class CustomUser(AbstractUser):
    """
    The User model has already:
    - first name
    - last name
    - email
    - username
    - is_active
    - is_staff
    - date_joined
    - last_login
    """

    phone = models.CharField(max_length=35, blank=True, null=True)
    address = models.CharField(max_length=255, blank=True, null=True)
    address_number = models.CharField(max_length=35, blank=True, null=True)
    city = models.CharField(max_length=35, blank=True, null=True)

```

Once it's done, you'll need to add a manager. The manager will tell Django how to create a new user or a super user. 

```python
// Some codefrom django.contrib.auth.models import AbstractUser, BaseUserManager
from django.conf import settings
from django.utils.translation import ugettext_lazy as _


class ProfileManager(BaseUserManager):

    def create_user(self, email, username, password, **extra_fields):
        """
        Create and save a User with the given username, email and password.
        """
        if not email:
            raise ValueError(_('The Email must be set'))
        email = self.normalize_email(email)
        user = self.model(email=email, username=username, **extra_fields)
        user.set_password(password)
        user.save()
        return user

    def create_superuser(self, email, username, password, **extra_fields):
        """
        Create and save a SuperUser with the given username, email and password.
        """
        extra_fields.setdefault('is_staff', True)
        extra_fields.setdefault('is_superuser', True)
        extra_fields.setdefault('is_active', True)

        if extra_fields.get('is_staff') is not True:
            raise ValueError(_('Superuser must have is_staff=True.'))
        if extra_fields.get('is_superuser') is not True:
            raise ValueError(_('Superuser must have is_superuser=True.'))
        return self.create_user(email=email, password=password, username=username, **extra_fields)
```

  
