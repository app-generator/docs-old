---
description: Getting Started with Flask
---

# Install a working [User Profile](https://flask-dashboard-material-pro.appseed.us/user)

**User Profile** is a page common to many Admin Dashboards here. 

In this quick tutorial I will use the Material PRO Bootstrap Template so that you can get started quickly and easily, with the ability to reuse this approach and code on other pages that also use WTFORMs, SQLAlchemy Models, and other tools commonly used in the AppSeed.us configuration.

This tutorial assumes you have installed Flask and the AppSeed template for Material, Material PRO, or any Admin Dashboard that has a User Profile page

First, your Jinga2 User Profile page, should be located in the /app/home/templates folder. I am running on Windows machine so my file names appear with forward slashes and filenames are not case-sensitive, where a UNIX-OS workstation is going show back-slashes and have case-sensitive filenames. I've added a couple of additional database fields, that you might want to also consider, but here is a basic that works with the AppSeed.us template.

First, a picture is worth a thousand words, here is what this code looks like once built ...

## A picture is worth a thousand words, here is what this code looks like when implemented ...

![AppSeed Docs - Edit on Github Option.](https://raw.githubusercontent.com/app-generator/docs/master/static/Profile_Page.jpg)

Four files need editing to make this work:

1. page-user.html - The Jinja2 template html
2. models.py
3. routes.py
4. forms.py

## #1 page-user.html

Let's begin by editing the /app/home/templates/page-user.html file (or similar - there be a minor name or location variation on your admin dashboard) 

```bash
{% extends "base-site.html" %}

{% block title %} Page User {% endblock %} 

<!-- Specific Page CSS goes HERE  -->
{% block stylesheets %}{% endblock stylesheets %}

{% block content %}

          <div class="row">
            <div class="col-md-8">
              <div class="card">
                <div class="card-header card-header-primary">
                  <h4 class="card-title">Edit Profile</h4>
                  <p class="card-category">Complete your profile</p>
                </div>
                <div class="card-body">
                  <form class="form" method="post" action="/profile">

                    {{ form.hidden_tag() }}

                    <div class="row">
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Username</label>
                          {{ form.username(class="form-control", value = current_user.username ) }}
                          <!-- <input type="text" class="form-control" value="{{ current_user.username }}"> -->
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Email address</label>
                          {{ form.email(class="form-control", value = current_user.email) }}
                          <!-- <input type="email" class="form-control" value="{{ current_user.email }}"> -->
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          {% if msg %}
                            <h4 class="text-danger">{{ msg | safe }}</h4>
                          {% else %}
                            <h4 class="mt-3" align="center">Profile Update Page</h4>
                          {% endif %} 
                        </div>
                      </div>
                      
                    </div>
                    <div class="row">
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">First Name</label>
                          {{ form.firstname(class="form-control", value = current_user.firstname) }}
                          <!-- <input type="text" class="form-control"  value="{{ current_user.firstname }}"> -->
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Last Name</label>
                          {{ form.lastname(class="form-control", value = current_user.lastname) }}
                          <!-- <input type="text" class="form-control" value="{{ current_user.lastname }}"> -->
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Title</label>
                          {{ form.title(class="form-control", value = current_user.title) }}
                          <!-- <input type="text" class="form-control" value="{{ current_user.lastname }}"> -->
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-12">
                        <div class="form-group">
                          <label class="bmd-label-floating">Address</label>
                          {{ form.address(class="form-control", value = current_user.address) }}
                          <!-- <input type="text" class="form-control"  value="{{ current_user.address }}"> -->
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">City</label>
                          {{ form.city(class="form-control", value = current_user.city) }}
                          <!-- <input type="text" class="form-control" value="{{ current_user.city }}"> -->
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Country</label>
                          {{ form.country(class="form-control", value = current_user.country) }}
                          <!-- <input type="text" class="form-control" value="{{ current_user.country }}"> -->
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Postal Code</label>
                          {{ form.postzip(class="form-control", value = current_user.postzip) }}
                          <!-- <input type="text" class="form-control" value="{{ current_user.postzip }}" > -->
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Web URL</label>
                          {{ form.weburl(class="form-control", value = current_user.weburl) }}
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Linkedin</label>
                          {{ form.linkedin_url(class="form-control", value = current_user.linkedin_url) }}
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Twitter</label>
                          {{ form.twitter(class="form-control", value = current_user.twitter) }}
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Skype</label>
                          {{ form.skype_id(class="form-control", value = current_user.skype_id) }}
                        </div>
                      </div>
                      <div class="col-md-4">
                        <div class="form-group">
                          <label class="bmd-label-floating">Phone</label>
                          {{ form.phone(class="form-control", value = current_user.phone) }}
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-12">
                        <div class="form-group">
                          <label>About Me</label>
                          <div class="form-group">
                            <label class="bmd-label-floating"> </label>
                            {{ form.about(class="form-control", value = current_user.about ) }}
                            <!-- <input type="text" class="form-control" value="{{ current_user.about }}" rows="5" >  -->
                            <!-- <textarea class="form-control" rows="5"></textarea> -->
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-12">
                        <div class="form-group">
                          <label>Profile</label>
                          <div class="form-group">
                            <label class="bmd-label-floating"> </label>
                            {{ form.profile(class="form-control", value = current_user.profile) }}
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="col-md-3 col-sm-4">
                      <h4 class="title">Avatar</h4>
                      <div class="fileinput fileinput-new text-center" data-provides="fileinput">
                        <div class="fileinput-new thumbnail img-circle">
                          <img class="img" src="/static/assets/img/faces/{{ current_user.photo }}" />
                        </div>
                        <div class="fileinput-preview fileinput-exists thumbnail img-circle"></div>
                        <div>
                          <span class="btn btn-round btn-rose btn-file">
                            <span class="fileinput-new">Add Photo</span>
                            <span class="fileinput-exists">Change</span>
                            <!-- <input type="file" name="..." /> -->
                            {{ form.photo(type = "file", value = "/static/assets/img/faces/"+current_user.photo ) }}
                            <input type="hidden" value="{{current_user.photo}}" name="oldphoto">
                          </span>
                          <br />
                          <a href="#pablo" class="btn btn-danger btn-round fileinput-exists" data-dismiss="fileinput"><i class="fa fa-times"></i> Remove</a>
                        </div>
                      </div>
                    </div>
                  
                    <button type="submit" name="profile" class="btn btn-primary pull-right">Update Profile</button>
                    <div class="clearfix"></div>
                  </form>
                </div>
              </div>
            </div>
            <div class="col-md-4">
              <div class="card card-profile">
                <div class="card-avatar">
                  <a href="#pablo">
                    <img class="img" src="/static/assets/img/faces/{{ current_user.photo }}" />
                  </a>
                </div>
                <div class="card-body">
                  <h6 class="card-category text-gray">
                    {{ current_user.username }}
                  </h6>
                  <h4 class="card-title">
                    {{ current_user.email }}
                  </h4>
                  <p class="card-description">
                    {{ current_user.profile }}
                  </p>
                  <a href="#pablo" class="btn btn-primary btn-round">Follow</a>
                </div>
              </div>
            </div>
          </div>

{% endblock content %}

<!-- Specific Page JS goes HERE  -->
{% block javascripts %}{% endblock javascripts %}
```

## 2. models.py

Note that I use MySQL and decided to add SQLAchemy dialects, where you probably should not. Using dialects precludes you from hosting your website with providers that don't support the specific database - MySQL in this example.

Exclude the line "from sqlalchemy.dialects.mysql import TIMESTAMP, DATETIME, FLOAT, JSON, TINYINT" if you want to use non-specific databases like the default SQLite (development) and Postgres (production). I left it here so you can see what to do in a situation where dialects make sense for you only.

This models.py configuration is used by the SQLAlchecy db.create_all() instruction located in the AppSeed /app/__init__.py script will create an empty User table in the database based on the configuration information you provide in your /config.py file

```bash
"""
License: MIT
Copyright (c) 2019 - present AppSeed.us
"""

from flask_login import UserMixin
from sqlalchemy import Binary, Column, Integer, String
from sqlalchemy.dialects.mysql import TIMESTAMP, DATETIME, FLOAT, JSON, TINYINT
    # from https://docs.sqlalchemy.org/en/13/dialects/mysql.html#timestamp-columns-and-null
    # BIGINT, BINARY, BIT, BLOB, BOOLEAN, CHAR, DATE, \
    # DATETIME, DECIMAL, DECIMAL, DOUBLE, ENUM, FLOAT, INTEGER, \
    # LONGBLOB, LONGTEXT, MEDIUMBLOB, MEDIUMINT, MEDIUMTEXT, NCHAR, \
    # NUMERIC, NVARCHAR, REAL, SET, SMALLINT, TEXT, TIME, TIMESTAMP, \
    # TINYBLOB, TINYINT, TINYTEXT, VARBINARY, VARCHAR, YEAR

from app import db, login_manager

from app.base.util import hash_pass

class User(db.Model, UserMixin):

    __tablename__ = 'User'

    # class User(db.Model):
    # id = db.Column(db.Integer, primary_key=True)
    # username = db.Column(db.String(80), unique=True, nullable=False)
    # email = db.Column(db.String(120), unique=True, nullable=False)

    id = Column(Integer, primary_key=True, autoincrement=True)
    username = Column(String(22), primary_key=True, unique=True)
    email = Column(String(120), unique=True, nullable=False)
    password = Column(Binary)
    firstname = Column(String(25))
    lastname = Column(String(32))
    address = Column(String(75))
    city = Column(String(22))
    country = Column(String(22))
    postzip = Column(String(8))
    about = Column(String(500))
    profile = Column(String(350))
    title = Column(String(60))
    last_ind = Column(String(20))
    address2 = Column(String(45))
    email_id2 = Column(String(120), unique=True)
    weburl = Column(String(120))
    linkedin_url = Column(String(60))
    skype_id = Column(String(22))
    photo = Column(String(60))
    title = Column(String(140))
    weburl = Column(String(140))
    linkedin_url = Column(String(140))
    twitter = Column(String(32))
    skype_id = Column(String(40))
    phone = Column(String(35))
```

So far so good ...

## 3. routes.py

There will be a routes.py located in your app/base directory - and in your app/home directory. 
a. If you add this new route to app/base/routes.py, only the addition of the app.base.forms UserDetailForm is required 
```bash
from app.base.forms import LoginForm, CreateAccountForm, UserDetailForm
```
b. If you want to add this route to app/home/routes.py, ensure that you have added a couple of additional lines that the new route script needs, as follows:

##In /app/home/routes.py
```bash
from flask import json, render_template, redirect, url_for, jsonify, request
from flask_login import login_required, current_user, login_user, logout_user
from app import db, login_manager
from app.home.forms import UserDetailForm  
from app.base.models import User, Country, Indicator
```
You might not need to import flask_login's login_user, logout_user here, so you can do a little testing and remove them if unneeded. Again, these additions to /app/home/routes.py are only needed if you want to add the new route to the home routes file.

Now you can add the following route to whichever routes.py file you prefer.new add UserDetailForm after the Login and Create_user forms 

```bash
@blueprint.route('/profile', methods=['GET', 'POST'])
@login_required
def profile():
    
    user_detail_form = UserDetailForm(request.form)
    if 'profile' in request.form:

        username  = request.form['username']
        
        #added hidden form oldphoto because the photo utility didn't pass the photo filename
        photo = request.form['photo']
        oldphoto = request.form['oldphoto']
        if photo == "":
            photo = oldphoto
        
        # user = User(**request.form)   # This is the script used by /login and /create_user (register)
        # firstname = request.form['firstname']

        User.query.filter_by(username=username).update({
            'email':request.form['email'],
            'firstname':request.form['firstname'],
            'lastname':request.form['lastname'],
            'address':request.form['address'],
            'city':request.form['city'],
            'country':request.form['country'],
            'postzip':request.form['postzip'],
            'about':request.form['about'],
            'profile':request.form['profile'],
            'title':request.form['title'],
            'weburl':request.form['weburl'],
            'linkedin_url':request.form['linkedin_url'],
            'skype_id':request.form['skype_id'],
            'photo':photo,
            'weburl':request.form['weburl'],
            'linkedin_url':request.form['linkedin_url'],
            'twitter':request.form['twitter'],
            'skype_id':request.form['skype_id'],
            'phone':request.form['phone']
        })  # There might be a better way using the **request.form bulk load approach noted above, let us know
        
        db.session.commit()
        return render_template( 'page-user.html', msg='Profile changes made', form=user_detail_form)

    else:
        sidetog = 'profile'
        return render_template( 'page-user.html', value = sidetog, form=user_detail_form)
```

## 4. forms.py

This just leaves the forms.py file. Again you can chose to create a new forms.py file in the home directory - or to leave it in the base. If you add your new route above  to map to it at the top of the routes.py file with the line "from app.home.forms import UserDetailForm". I chose this latter option, but you might prefer to add the UserDetailForm in the /app/base directory.

Here is what the new form looks like:
```hash
class UserDetailForm(FlaskForm):
    username = TextField('Username'     , id='username' , validators=[DataRequired()])
    email    = TextField('Email'        , id='email'    , validators=[DataRequired(), Email()])
    password = PasswordField('Password' , id='pwd'      , validators=[DataRequired()])
    firstname = TextField('firstname'     , id='firstname' )
    lastname = TextField('lastname'     , id='lastname' )
    address = TextField('address'     , id='address' )
    city = TextField('city'     , id='city' )
    country = TextField('country'     , id='country' )
    postzip = TextField('postzip'     , id='postzip' )
    about = TextField('about', id='about')
    profile = TextField('profile'     , id='profile' )
    title = TextField('title'     , id='title' )
    weburl = TextField('weburl'     , id='weburl' )
    linkedin_url = TextField('linkedin_url'     , id='linkedin_url' )
    twitter = TextField('twitter'     , id='twitter' )
    skype_id = TextField('skype_id'     , id='skype_id' )
    photo = TextField('photo', id='photo')
    phone = TextField('phone'     , id='phone' )
```

That's it. Enjoy!

## If you want to include data from other tables - rather than Flask_login's current_user.<?> array, look to the following [tutorial](https://www.codementor.io/@garethdwyer/building-a-crud-application-with-flask-and-sqlalchemy-dm3wv7yu2)
