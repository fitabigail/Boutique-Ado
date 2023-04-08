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




