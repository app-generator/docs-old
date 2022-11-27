---
description: >-
  Dashboard built by AppSeed in Django on top of Soft Dashboard PRO - Manual Coded Version.
---

# [Django Soft Dashboard ENH](https://appseed.us/product/soft-ui-dashboard-pro/django/)

This product is manualy coded on top of the generated version [Soft Dashboard PRO](./soft-ui-dashboard-pro.md)


> Version: **v1.0.5** - release date `2022-07-14`

* UI Kit: **Soft Dashboard PRO** (Premium version)
* Bootstrap 5 Design (no jQuery dependency)
  * `Light/Dark Mode`
  * 50+ pages: `Charts`, Dashboards, `Multiple Layouts`
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

* 👉 [Django Soft Dashboard PRO](https://appseed.us/product/soft-ui-dashboard-pro/django/) - product page
* 👉 Premium [Support](https://appseed.us/support) (Email and LIVE on Discord)



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
