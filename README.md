## **install django**
- pip3 install Django==3.2

## **start project**
- django-admin startproject botique_ado .

## **migrate**
- python3 manage.py migrate

## **create super user**
- python3 manage.py createsuperuser

## **env.py**
- touch env.py

## **secret key env.py**
import os

os.environ["SECRET_KEY"] = ""

## **secret key settings.py**
- import os
- if os.path.isfile('env.py'):
    import env

- SECRET_KEY = os.environ.get('SECRET_KEY')   

## **requirements.txt** 
- pip3 freeze --local > requirements.txt

## **runserver**
- python3 manage.py runserver

## ** add to gitignore
*.sqlite3
*.pyc

## **allauth** install

- pip3 install django-allauth==0.41.0
- installed allauth apps: 
'django.contrib.sites',
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
- authentication backend:
 Needed to login by username in Django admin, regardless of `allauth`, `allauth` specific authentication methods, such as login by e-mail
 
 AUTHENTICATION_BACKENDS = (
    
    'django.contrib.auth.backends.ModelBackend',
    
    'allauth.account.auth_backends.AuthenticationBackend',
)

SITE_ID = 1

EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'

ACCOUNT_AUTHENTICATION_METHOD = 'username_email'
ACCOUNT_EMAIL_REQUIRED = True
ACCOUNT_EMAIL_VERIFICATION = 'mandatory'
ACCOUNT_SIGNUP_EMAIL_ENTER_TWICE = True
ACCOUNT_USERNAME_MIN_LENGTH = 4
LOGIN_URL = '/accounts/login/'
LOGIN_REDIRECT_URL = '/'
   
- urls: path('accounts/', include('allauth.urls')),

## **requirements.txt** 
- pip3 freeze --local > requirements.txt
## migrate
- python3 manage.py migrate

## addmin sites
 - change the domain name and display name

## for testing purpose only
 - add success to : LOGIN_REDIRECT_URL = '/success' on settings.py
 - add email account verified and primary on addmin panel
 - must be logout from admin panel and search for /accounts/login page

## create templates folder and allauth
- mkdir templates 
- mkdir templates/allauth 

## bootstrap 4 template

- Bootstrap 4 documentation, which you can find [here](https://getbootstrap.com/docs/4.6/getting-started/introduction/)
- The Bootstrap Github Repository can be accessed [here](https://github.com/twbs/bootstrap)
- minified jQuery library: <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
- all the features :<script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js" integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0=" crossorigin="anonymous"></script>
**Note**: Make sure you change the line above in the same place where the Starter Template has it. The jQuery library must be loaded before Popper and Bootstrap for everything to work correctly.

- cp -r ../.pip-modules/lib/python3.8/site-packages/allauth/templates/* ./templates/allauth/
**note** for python version write python and tap tab
- create base.html on templates
- from bootstratp documantation get  **Starter template** [here](https://getbootstrap.com/docs/4.6/getting-started/introduction/)
- add meta <meta http-equiv="X-UA-Compatible" content="ie=edge"> - allowed suport for older edge versions

- add to the head under css :
        <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>

## base.html
- make page dynamic and add blocks for better structure : {% load static %}

## start app:
- python3 manage.py startapp home
- create home/ template/home folders: mkdir -p home/templates/home
- on home folder create index.html
- on index.html extend base : {% extends "base.html" %}
- create view
- create urls
- include home app to main urls.py file
- add app name to instaled apps on settings.py
- add on Directories :
'DIRS': [
            os.path.join(BASE_DIR, 'templates'),
            os.path.join(BASE_DIR, 'templates', 'allauth'),
        ],
- add content to inde.html
- add main page header to base.html
- create mkdir static
- create mkdir media
- create mkdir static/css
- add style 
- link base.html with base.css, fontawesome and add google fonts
- add to settings.py the static file route and media 
- add to botique_ado urls : from django.conf import settings and from django.conf.urls.static import static + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
