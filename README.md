

``` sudo pip3 install Django 1.11.7 ```

``` django-admin startproject django_auth . ```

``` django-admin startapp accounts ```

In "django_auth" > "settings.py" > INSTALLED_APPS, add:

``` accounts ```

And in ALLOWED_HOSTS, add:

``` ALLOWED_HOSTS = [os.environ.get('C9_HOSTNAME')] ```

Show home in favourites > .bashrc_aliases:

``` alias run="python3 manage.py runserver $IP:$PORT" ```

Now run:

``` . ~/.bash-aliases ```

``` python3 manage.py migrate ```

ADMIN LOGIN

``` python3 manage.py createsuperuser ```

Now run the app and add '/admin' to the end of the URL.

Create a new folder called templates and create an index.html file.

Add the following:

```
<!DOCTYPE html>
<html>
    <head>
        <title>Django Auth</title>
    </head>
</html>
<body>
    <nav>
        <ul>
            <li>
                <a href="#">Login</a>
            </li>
            <li>
                <a href="#">Logout</a>
            </li>
            <li>
                <a href="#">Register</a>
            </li>
            <li>
                <a href="#">Profile</a>
            </li>
        </ul>
    </nav>
</body>
```

In views.py, add the following:

```
def index(request):
    """Return the index.html file"""
    return render(request, 'index.html')
```

In urls.py, add the following:
```
from django.contrib import admin
from django.conf.urls import url
from django.urls import path
from accounts.views import index

urlpatterns = [
    path('admin/', admin.site.urls),
    url(r'$^', index)
]
```

INSTALL BOOTSTRAP:

``` sudo pip3 install django_forms_bootstrap ```

Updated Installed_apps:

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django_forms_bootstrap',
    'accounts',
]
```