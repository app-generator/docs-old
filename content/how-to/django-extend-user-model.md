---
description: How to extend the default user model in Django with more fields
---
# Django Extend User Model

This page explains how to extend the default User Model in Django and associate with a user other information like address, phone number .. etc.

Django provides a User model you can use for authentication or authorization. 

But what if you need more fields? Such as address, phone number, age ...etc. In that case, you can just extend the user model, here the `AbstractUser` class.

```
class Profile(AbstractUser):
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

    email = models.EmailField(db_index=True, unique=True)
    phone = models.CharField(max_length=35, blank=True, null=True)
    address = models.CharField(max_length=255, blank=True, null=True)
    address_number = models.CharField(max_length=35, blank=True, null=True)
    city = models.CharField(max_length=35, blank=True, null=True)
    country = models.CharField(max_length=35, blank=True, null=True)
    zip = models.CharField(max_length=35, blank=True, null=True)
    state = models.CharField(max_length=35, blank=True, null=True)
    user_photo = models.ImageField(upload_to=settings.DEFAULT_FILE_IMAGE_STORAGE, null=True, blank=True)

    objects = ProfileManager()

```



  
