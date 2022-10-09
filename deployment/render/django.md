---
description: How to deploy Django to Render Deployment Platform
---

# Deploy Django to Render

@Todo - General information Render Platform

> Topics covered

* `Render` Account Creation
* `Render` Account Settings
* The project to be deployed
* `Render` Environment set up
* `Render` Domain settings
* `Render` SSL certificates
* `Render` LIVE Service monitoring \


## `Render` Account Creation

Render provide Social auth and email auth, based on your preference you can sign up with Render

**IMG\_render\_signup**



Once successfully signed up, the user is redirected Render dashboard and sees the screen like below:

**IMG\_render\_dashboard**



## `Render` Account Settings

The Next step is to connect the Render account with the GitHub account, If you sign up with GitHub then this step is automatically done.

**IMG\_render\_account\_settings** \


## The project to be deployed

Source project: https://github.com/app-generator/django-react-soft-dashboard\


To deploy the Django app on Render we need to choose the **Web Service** option from the Dashboard as shown below:

**IMG\_render\_dashboard\_web\_service**

****

After selecting the web service option, the next step is to connect the GitHub project repository.  On the next page, we can select the project from the linked account, with private or public visibility.

**IMG\_render\_web\_service**

****

The next step is to edit deployment details. Here are the sections that need editing:

* **Name**: In this section, we should use a unique name for the web service.
* **Root Directory**:  By default, the root directory is set to the top-level directory in your repository. We have also the possibility to select subfolders in case the project structure is modular and for instance, the backend and the frontend use different directories
* **Environment**: In this section, we should select the language used to code the product, Python in our case.
* **Region**:- The region where your web service runs, not required to update by default is `Oregon (US West)`
* **Branch**:- The repository branch used for your web service.
* **Build Command**: The shell script that executes all the steps to build the project
* **Start Command**: This section informs Gunicorn where to locate the entry point in our Django starter: `gunicorn core.wsgi:application`
* **Add Environment Variables** required by the starter in `Advanced` section.
  * Python Version: `PYTHON_VERSION` = `3.10.4`
  * `GUNICORN_CMD_ARGS` = `--preload --bind=0.0.0.0:2000`
  * `PORT` = `2000`
  * `DJANGO_ALLOWED_HOSTS` = `.onrender.com`
* **Auto-Deploy**: Render provide this option to trigger a new deployment on every push to the repository. In case this feature is not useful, set this option to "NO" for manually managed deployments

With all the above settings specified as per project requirements, we can confirm the action and actually Create the new Service. 

**IMG\_render\_django\_deployment\_settings** \


## `Render` Domain settings

Render by default provides the domain itself, but the user can set up a custom domain based as well. For more information feel free to access the official documentation regarding [custom domains](https://render.com/docs/custom-domains). \


## `Render` SSL certificates

Render Platform provides valid SSL certificates for all managed services, and also offers the possibility to customize the certificates. \


## `Render` LIVE Service monitoring

Once the project is deployed, the users have the possibility to set up alerts in Health & Alerts section (Project Settings).

The `Health Check Path`  is the public URL of the project that should return a 200 status code on access.

Another option is to get notified via Email in case of Service failure. \


## Links & Resources

* [Render Django deployment](https://render.com/docs/deploy-django) - Official Guide to deploy Django app on Render
* [Custom domains on render](https://render.com/docs/custom-domains) - Official Guide to setup custom domain
* [Shell Script](https://www.shellscript.sh/) - Official Guide to shell script
* [Django](https://www.djangoproject.com/) - Official Guide to Django Framework
* [Gunicorn](https://gunicorn.org/) - Official Guide to Gunicorn
