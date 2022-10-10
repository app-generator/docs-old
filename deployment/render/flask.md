---
description: How to go LIVE with a Flask project using Render Deployment Platform
---

# Deploy Flask to Render

This page explains how to go live with a **Flask** project on **Render**, a popular deployment platform. For newcomers, [Render](https://render.com/) supports the deployment for all major languages, Free Certificates, DDoS protection, and auto deploys from GitHub.

> The VIDEO version - published on YouTube

{% embed url="https://youtu.be/jWxYzKVkcwY" %}
How to deploy Flask on Render Platform
{% endembed %}

### Render Account Creation

The Sign UP is provided via classic Email and Social Authentication for well-known providers like GitHub, GitLab, or Google. Once the sign-up process is finished, the user is redirected to the dashboard.

<figure><img src="../../.gitbook/assets/render-01-sign-up-page-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Sign UP page</p></figcaption></figure>

### Create a new project

All projects that use a dynamic language during runtime (Python, NodeJs) should be created as web services. This option can be found in the navigation bar, as shown below:

<figure><img src="../../.gitbook/assets/render-02-create-web-service-menu-min (1).jpg" alt=""><figcaption><p>Flask Render Deployment - Creat Web Service</p></figcaption></figure>

### Link GitHub Repository

The next step is to associate a Flask project with the newly created web service. Render support account linkage with external platforms like GitHub, GitLab, and BitBucket. In our demonstration, an open-source repository is used as a working sample.

> 👉 [Flask & Stripe - Mini eCommerce](https://github.com/app-generator/sample-flask-stripe) (MIT License)  

<figure><img src="../../.gitbook/assets/render-02-create-web-service-sshot-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Target Project</p></figcaption></figure>

> 👉 Here is the **Render** UI that allows the project association with the web service

<figure><img src="../../.gitbook/assets/render-03-create-web-service-link-repo-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Associate Repository</p></figcaption></figure>

### The project settings

Before going LIVE, we need to configure the future web service. Here is the information required by Render:

* ✅ The **name of the project** (mandatory)
* ✅ The **root** of the project (leave it blank)
* ✅ **Environment**: for a Flask project, we should select Python
* ✅ **Region**: only if the location of the server is relevant
* ✅ **Source Branch**: the main branch is used
* ✅ **Build Command**: a simple [BASH script](https://github.com/app-generator/sample-flask-stripe/blob/master/build.sh) is used
* ✅ **Start Command**: the entry point, usually managed by [Gunicorn](https://gunicorn.org/)

A visual representation of the above settings used to deploy the project can be found below:

<figure><img src="../../.gitbook/assets/render-04-create-web-service-basic-options-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Project Settings</p></figcaption></figure>

**The next step** is to specify the billing plan for the project. **Render** platform, at the moment this material is edited, provides a free plan only for static sites built with **React**, **Vue**, **Next**, and all other frameworks. 

<figure><img src="../../.gitbook/assets/render-05-create-web-service-plans-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Paid Pricing Plan</p></figcaption></figure>

The last step in this tutorial is to expand the "Advanced" section and provide a few **Environment variables** required by **Flask** and the Stripe feature.

* ✅ **Debug** Flag: False (the recommended value in production)
* ✅ [SECRET\_KEY](https://flask.palletsprojects.com/en/2.2.x/config/#SECRET\_KEY) variable: used to sign session secrets
* ✅ **SERVER\_ADDRESS**: Used by Stripe to redirect after a payment
* ✅ **Stripe Secrets:** PRIVATE and PUBLIC keys (provided by Stripe)

<figure><img src="../../.gitbook/assets/render-06-create-web-service-env-variables-min.jpg" alt=""><figcaption><p>Flask Render Deployment - App Environment Variables</p></figcaption></figure>

An important aspect of the build is the **automatic deployment** that is enabled by default. In this sample, a manual build is used, just to have full control over the deployment flow.

<figure><img src="../../.gitbook/assets/render-07-create-web-service-confirm-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Auto-Deploy Option</p></figcaption></figure>

***

<figure><img src="../../.gitbook/assets/render-08-create-web-service-deploy-console-min.jpg" alt=""><figcaption><p>Flask Render Deployment - First Deployment</p></figcaption></figure>

### Trigger Manual Deployment

The LIVE version of the project can be updated and even rollbacked anytime with ease via the UI. Here are the steps required by the LIVE update:

* ✅ Access **Manual Deploy** Option
* ✅ Select Deploy a specific commit
* ✅ Add the commit HASH to be used (provided by Github)
* ✅ Confirm/select the commit
* ✅ Confirm the action and trigger the deploy

> 👉 **Step #1 -** Select Specific Deployment Option

<figure><img src="../../.gitbook/assets/render-09-create-web-service-trigger-manual-build-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Manual Deploy (Step 1)</p></figcaption></figure>

> 👉 **Step #2** - Select the GitHub commit to deploy

<figure><img src="../../.gitbook/assets/render-10-create-web-service-trigger-build-commit-id-min.jpg" alt=""><figcaption><p>Flask Render Deployment - Manual Deploy, Select Commit</p></figcaption></figure>

Once the **Render** platform starts the build, the state of the web service is flagged as "**IN Progress**" and soon the updated version should be LIVE. 

## Links & Resources

* 👉 Deployment [support](https://appseed.us/support/) provided by [AppSeed](https://appseed.us/)
* 👉 [Render](https://render.com/) - the official platform documentation
* 👉 [Flask Stripe Sample](https://github.com/app-generator/sample-flask-stripe) - the project used in this material
