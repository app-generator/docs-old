---
description: How to deploy Django to Render Deployment Platform
---

# Deploy Django to Render Deployment Platform

@Todo - General information Render Platform

> Topics covered

- `Render` Account Creation 
- `Render` Account Settings 
- The project to be deployed
- `Render` Environment set up
- `Render` Domain settings
- `Render` SSL certificates
- `Render` LIVE Service monitoring

<br />

## `Render` Account Creation

- Render provide Social auth and email auth, based on your preference you can sign up with render 

![Render Sign up](/.gitbook/assets/render_signup.png)

- Once successfully sign up and login, you will be redirect to Render dashboard and see the screen like bellow 

![Render dashboard](/.gitbook/assets/render_dashboard.png)

<br />

## `Render` Account Settings 

- Next step is connect Render account with github account, If you sign up with github then this step is automatically done.

![Render account settings](/.gitbook/assets/render_account_settings.png)

<br /> 

## The project to be deployed

Source project: https://github.com/app-generator/django-react-soft-dashboard

<br /> 

- To deploy Django app on render you required to choose Web service option on dashboard

![Render account settings](/.gitbook/assets/render_dashboard_web_service.png)

- After selection web service, required to connect github project repository.
- there are two options, First you can choose private repository from your linked github account. Or second you can connect with github public project repository

![Render web service](/.gitbook/assets/render_web_service.png)

- Next required to setup project's setting's
    - Name:- In this section you required to enter a unique name for your web service.
    - Root Directory:- By default, the root directory is set to the top-level directory in your repository. if your project github repository follow mono repo structure then you required to enter sub directory of project
    - Environment:- You required to choose Python3 option because this project and used used library is build based on Python3 language.
    - Region:- The region where your web service runs, not required to update by default is `Oregon (US West)`
    - Branch:- The repository branch used for your web service.
    - Build Command:- created shell script file named `build.sh` to build project. to refer this file as a build command enter `./build.sh`
    - Start Command:- to start project with gunicorn python web server enter command `gunicorn core.wsgi:application`

    - To set environment variable there is option `Add Environment Variable` in `Advanced` section.
    - Python version is specify by environment variable named `PYTHON_VERSION` = `3.10.4`
    - other variable to set
        - `GUNICORN_CMD_ARGS` = `--preload --bind=0.0.0.0:2000`
        - `PORT` = `2000`
        - `DJANGO_ALLOWED_HOSTS` = `.onrender.com`
    - Auto-Deploy:- Render provide Automatic deploy on every push to your repository or changes to your service? Select "No" to handle your deploys manually.
    - once you done with all above setting's, at last click on `Create Web Service`

![Render django_web_service_settings](/.gitbook/assets/render_django_deployment_settings.png)

<br />

## `Render` Domain settings

- Render by default provide domain it self, if required you can setup custom domain based on requirement.
* [custom domains](https://render.com/docs/custom-domains) - Official Guide to setup custom domain

<br />

## `Render` SSL certificates

- Render by default manage SSL certificates, if required you can customize certificates. 

<br />

## `Render` LIVE Service monitoring

- once project is deployed, you can setup Health & Alerts in project setting's section.
- first required to enter `Health Check Path` url of your project that return 200 status code.
- second setup Service Failure Notifications to `Email`

<br />

## Links & Resources

* [Render Django deployment](https://render.com/docs/deploy-django) - Official Guide to deploy Django app on render
* [custom domains on render](https://render.com/docs/custom-domains) - Official Guide to setup custom domain
* [Shell Script](https://www.shellscript.sh/) - Official Guide to shell script
* [Django](https://www.djangoproject.com/) - Official Guide to Django Framework
* [Gunicorn](https://gunicorn.org/) - Official Guide to Gunicorn
