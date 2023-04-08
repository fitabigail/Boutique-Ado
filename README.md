/**install django**/
- pip3 install Django==3.2
/**start project**/
- django-admin startproject botique_ado .
/**migrate**/
- python3 manage.py migrate
/**create super user**/
- python3 manage.py createsuperuser
/**env.py**/
- touch env.py
/**secret key env.py**/
import os

os.environ["SECRET_KEY"] = ""
/**secret key settings.py**/
- import os
- if os.path.isfile('env.py'):
    import env

- SECRET_KEY = os.environ.get('SECRET_KEY')   
