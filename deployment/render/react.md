---
description: How to deploy React to Render Deployment Platform
---

# Deploy React to Render Deployment Platform

@Todo - General information Render Platform

> Topics covered

- `Render` Account Creation 
- `Render` Account Settings 
- The project to be deployed
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

- To deploy Django app on render you required to choose Static Sites option on dashboard

![Render account settings](/.gitbook/assets/render_dashboard_static_sites.png)

- After selection Static Sites, required to connect github project repository.
- there are two options, First you can choose private repository from your linked github account. Or second you can connect with github public project repository
![Render Static Sites](/.gitbook/assets/render_static_site.png)

- Next required to setup project's setting's
    - Name:- In this section you required to enter a unique name for your static site.
    - Root Directory:- By default, the root directory is set to the top-level directory in your repository. if your project github repository follow mono repo structure then you required to enter sub directory of project
    - Branch:- The repository branch used for your web service.
    - Build Command:- created shell script file named `build.sh` to build project. to refer this file as a build command enter `./build.sh`
    - Publish directory:- The relative path of the directory containing built assets to publish Examples: `./`, `./build`, `dist` and `frontend/build`.

    - To set environment variable there is option `Add Environment Variable` in `Advanced` section.
    - Auto-Deploy:- Render provide Automatic deploy on every push to your repository or changes to your service? Select "No" to handle your deploys manually.
    - once you done with all above setting's, at last click on `Create Static Site`

![Render django_web_service_settings](/.gitbook/assets/render_react_deployment_settings.png)

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

* [Render Django deployment](https://render.com/docs/deploy-vue-js) - Official Guide to deploy React app on render
* [custom domains on render](https://render.com/docs/custom-domains) - Official Guide to setup custom domain
* [Shell Script](https://www.shellscript.sh/) - Official Guide to shell script