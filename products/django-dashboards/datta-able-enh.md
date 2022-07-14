---
description: >-
  Dashboard built by AppSeed in Django on top of Datta Able design - Manual Coded Version.
---

# Django Datta Enhanced

This product is manualy coded on top of the generated version [Datta Able PRO](./datta-able-pro.md)

> Version: **v1.0.9** - release date `2022-07-10`

* UI Kit: [Datta Able PRO](https://appseed.us/product/datta-able/) (Premium version)
* Bootstrap 5 Design (no jQuery dependency)
  * `Light/Dark Mode`
  * 190 pages: `Charts`, Dashboards, `Multiple Layouts`
* SQLite Database, Django Native ORM
* Session-Based Authentication, Forms validation
* Deployment scripts: Docker, Gunicorn/Nginx
- Improved Authentication
  - Visual password strength indicator (registration)
  - Suspend user after 3 failed login attempts
- New Feature: `User Profiles`
  - Extended User profile
  - Added Superusers
  - Image upload via `FTP`

> Links

* 👉 [Datta Able Django PRO](https://appseed.us/product/datta-able-pro/django/) - product page
* 👉 [Datta Able Django PRO](https://django-datta-able-enh.appseed-srv1.com/) - LIVE Demo
* 👉 [Support](https://appseed.us/support) (Email and LIVE on Discord) for `registered users`.

{% embed url="https://www.youtube.com/watch?v=d8OqLGCzOuE" %}
Django Datta Able PRO - Presentation

{% endembed %}

## Improved Authentication 

The codebase has been update to support some new features: 

- Automatic user suspension on consecutive failed logins
  - Limit saved in `configuration` 
  - `Password strength` indicator (registration page)



## FTP Storage

The feature is activated via the `.env` settings. Sample configuration: 

```env
FTP_UPLOAD=True
upload_cloud_type=storages.backends.ftp.FTPStorage
ftp_username   = <FTP_USER>
ftp_password   = <FTP_PASS>
ftp_server_url = <FTP_SERVER_IP>
ftp_port       = <FTP_SERVER_PORT>
upload_url     = <WWW_ROOT_FOR_IMAGES>
```  



## Extended User Profile

- Users are able to edit their profile:
  - Full Name, address, phone number and ZIP Code
- Upload their profile image
  - If the `FTP_UPLOAD` feature is active



## Users Management

> Note: Feature reserved for `superusers`

- List all users
- Edit the information
- Suspend/unsuspend the users


## 🚀 Where to go from here

* 👉 Access the [support](https://appseed.us/support/) page in case something is missing
* 👉 Use [Datta Able Generator](https://appseed.us/generator/datta-able/) to generate a new project
