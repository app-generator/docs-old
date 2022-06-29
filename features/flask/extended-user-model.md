---
description: Learn how to code an extended user model in Flask
---

# Extended User Model

This page explains **how to code an extended user model** in Flask. Bsed on the code, a simple `User` model that manages only the authentication is enhanced with more features: Admin role, state (active & suspended), password strenght during the registration process

> Topics covered

* Starting from a simple starter
* Enhance the exising `User` model with roles and state (users can be supended or active)
* Add the new model `UserProfile` to manage other fields related to the user
  * `address`, `phone number`, `Full name`, `website`
* CLI improvements
  * to manage and migarte the database
  * create `admins`
* The UI changes
  * for ordinary users
  * for admins

\


## Starting from a simple starter

The codebase used during the demostration is Flask Datta Able, a simple and open-source starter.

\


## Enhance the exising `User` model

* Add new fields
* `role`, `status`, `failed_logins`\


## Add new `UserProfile` model

* UserProfile table fileds
* `full_name`,`bio`,`address`,`zipcode`,`phone`,`email`,`website`,`image`

\


## CLI improvements

* Used for database init & migration
  1. python manage.py db init (for create migrations)
  2. python manage.py db migrate (for apply migrations)
  3. python manage.py db create\_admin (for create admin user)
  4. python manage.py db runserver (for run app)

\


## relation with the parent (User model)

1. ForeignKey realtion with UserProfile

## Signals

1. Create Userprofile(function name: create\_profile\_by\_user)
2. Delete Userprofile(function name: delete\_profile\_by\_user)

\


## Routing updates

* `/register` (methods=\['GET', 'POST'])
* `/login` (methods=\['GET', 'POST'])
* `/profile` (methods=\['GET'])
* `/user_list` (methods=\['GET'])
* `/edit_user` (methods=\['GET', 'PUT'])
* `/update_status` (methods=\['PUT'])
* `/email_exists` (methods=\['GET'])
* `/delete_user` (methods=\['DELETE'])

\


## UI Changes

* Bootstrap model
  1. edit button popup model (for edit users details)
  2. edit button popup model (for user profile details)
  3. validate the password strength using a bar colored from red (week password) to green (strong password).
  4. status update toggle button (Active/Suspend)
  5. user edit email check valid or not
  6. delete user display popup (Do you want to delte)

\


## events front-end the backend

1. onchange (for status update)
2. onclick (for get user details and delete user)
3. onSubmit (for form submit)
4. onkeyUp (for check email exists or not)

\


## events from the backend

1.GET, POST, PUT, DELETE

\


## FTP Server

1. connect FTP server
2. upload image to save FTP server
3. save image url to db
4. get image to saved image url
