---
description: Learn how to manage users in Django with ease - tutorial for beginners.
---

# Django Auth System

Being a "batteries-included" framework, Django comes with a powerful authentication/authorization system that we can use and extend in our projects with ease. For those that start from nothing, feel free to access the resources mentioned below and come back here once the content is understood: 

* [How to install Django](django-how-to-install.md) - simple, tested steps to install Django
* [Django for beginners](django-for-beginners.md) - a comprehensive tutorial that covers the basics

> Topics covered in this tutorial

* `User` the table where the information is saved
* How to create a new user using the Django CLI
* How to create a `superuser` 
* How to `update the password` - Django CLI
* Create a user using forms

### User Model

As mentioned in the official Django documentation, the **User** model represents the core entity used to save and manage authentication. The fields managed by the User model can be found below:

| Field | Sample Value | Information |
| :--- | :--- | :--- |
| username | test | Mandatory Field |
| password | Super\_S3cret | optional for inactive users |
| email | test@appseed.us | optional |
| fist\_name | John | optional |
| last\_name | Doe | optional |

Probably the most simple way to create a new user in Django is to use the CLI \(Django shell\). In case you don't have already a Django project, feel free to clone an [open-source sample](https://github.com/app-generator/django-learn-by-coding) provided by the AppSeed Team to explain many Django concepts: 

```text
$ git clone https://github.com/app-generator/django-learn-by-coding.git
$ cd django-learn-by-coding
```

> Create a virtual environment - Linux-based systems

```text
$ virtualenv env
$ source env/bin/activate 
```

For Windows system, the syntax is different:

```text
$ virtualenv env
$ .\env\Scripts\activate 
```

> Install Django

```text
$ pip install django
```



### Create Users - Django CLI

The user creation process using the terminal is usually related to the `superuser` that allows us to access the `admin` section. For newcomers, the admin section manages the registered users, groups defined in our project. 

> Create the `superuser` in Django

```text
$ # We are in the ROOT of the project
$ python manage.py createsuperuser
sername (leave blank to use 'test'): admin
Email address: test@appseed.us
Password: ********
Password (again): ********
Superuser created successfully. 
```

Once the `superuser` admin is created we can access the `admin` section and interact with all models registered by our project. Let's explore the users using the Django CLI:

```python
>>> from django.contrib.auth.models import User 
>>> User.objects.all()                         
<QuerySet [<User: admin>]>
```

  We can see the new admin saved a few seconds ago. 

```python
>>> admin = User.objects.all()[0] # Slice - get the first object
>>> admin.id
1
>>> admin.username
'admin'
>>> admin.password
'pbkdf2_sha256$260000$g3i1kS5WQLQbeND5AS4CRD$Ekn9VOH9o0T6DsF5Vll5mZupslzwDjI348Q8eDwNeIw=' 
```

Using the CLI we can explore all properties and of course update fields. 

> Create a new \(common\) user

```python
>>> from django.contrib.auth.models import User
>>> user = User.objects.create_user('test', 'test@appseed.us', 'Super_S3cret111')
```

As we can see, new users can be created with ease using the `create-user` helper provided by `User` model - Let's check again all registered users:

```python
>>> >>> User.objects.all()         
<QuerySet [<User: admin>, <User: test>]>
```

 

### Create Users via UI

Using the console to create and manage users might be fun but might be also useful in our projects to allow users to register themselves using a public web page. To do this, we need a simple page where the form is exposed and a backend to handle the information sent to the user.

> Create the SignUp Form

```python
class SignUpForm(UserCreationForm):
    username = forms.CharField(
        widget=forms.TextInput(
            attrs={
                "placeholder" : "Username"
            }
        ))
    email = forms.EmailField(
        widget=forms.EmailInput(
            attrs={
                "placeholder" : "Email"
            }
        ))
    password1 = forms.CharField(
        widget=forms.PasswordInput(
            attrs={
                "placeholder" : "Password"
            }
        ))
    password2 = forms.CharField(
        widget=forms.PasswordInput(
            attrs={
                "placeholder" : "Password check"
            }
        ))
```

> Create the controller

```python
def register_user(request):

    # A user-friendly message 
    msg = None

    # User submits the credentials 
    if request.method == "POST":
        
        # Initialize the from POST data
        form = SignUpForm(request.POST)
        
        # Check all constraints (one line)
        if form.is_valid():
        
            # Create the user
            form.save()
            
            msg     = 'User created successfully.'
            
        else:
            msg = 'Form is not valid'    
    
    # Show the SignUp Page 
    else:
        form = SignUpForm()

    return render(request, "accounts/register.html", {"form": form, "msg" : msg })
```

> The page that shows the form and invite the user to register

```markup
<form role="form" method="post" action="">

    {% csrf_token %}                    

    <div>
        {{ form.username }}
    </div>
    <span class="text-error">{{ form.username.errors }}</span>

    <div>
        {{ form.email }}
    </div>
    <span class="text-error">{{ form.email.errors }}</span>

    <div>
        {{ form.password1 }}
    </div>
    <span class="text-error">{{ form.password1.errors }}</span>

    <div>
        {{ form.password2 }}
    </div>
    <span class="text-error">{{ form.password2.errors }}</span>
    
    <button type="submit" name="register">Register</button>

</form>
```

> The register mechanism

* The User sees the registration page
* The User inputs all fields 
* The form is submitted and the controller receives all information \(username, password\)
* If the form is valid, the form is `saved` and the user is created 
* A confirmation message is returned to the user

The above sample uses a form to create the user but we can update the code to use the `create-user` method as well:

```python
def register_user(request):

    # A user-friendly message 
    msg = None

    # User submits the credentials 
    if request.method == "POST":
        
        # Initialize the from POST data
        form = SignUpForm(request.POST)
        
        # Check all constraints (one line)
        if form.is_valid():
        
            username     = form.cleaned_data.get("username")  # <-- UPDATED      
            email        = form.cleaned_data.get("email")     # <-- UPDATED 
            raw_password = form.cleaned_data.get("password1") # <-- UPDATED
            
            # Create user: UPDATED
            new_user = User.objects.create_user(username, email, raw_password)
            
            msg     = 'User created successfully.'
            
        else:
            msg = 'Form is not valid'    
    
    # Show the SignUp Page 
    else:
        form = SignUpForm()

    return render(request, "accounts/register.html", {"form": form, "msg" : msg })
```



> Thanks for reading! For more topics, feel free to [contact](https://appseed.us/support) Appseed.



### Resources

* Read more about [Django](https://www.djangoproject.com/) \(official docs\)
* Start fast a new project using _development-ready_ [Django Starters](https://appseed.us/admin-dashboards/django) 

