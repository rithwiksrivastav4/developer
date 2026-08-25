# Django Complete Interview Preparation Guide (2 Years Experience)

## 1. Django Fundamentals

### What is Django?

Django is a high-level Python web framework used to build secure,
scalable web applications quickly.

### Django Features

-   MVT architecture
-   ORM
-   Authentication
-   Admin panel
-   Security features
-   URL routing
-   Template engine
-   REST API support

------------------------------------------------------------------------

# 2. Django Architecture (MVT)

    User Request

        |
        v

    URL Dispatcher

        |
        v

    View

        |
        v

    Model + Database

        |
        v

    Template

        |
        v

    Response

Components:

## Model

Handles database structure and data.

## View

Handles business logic.

## Template

Handles UI presentation.

------------------------------------------------------------------------

# 3. Django Project Setup

Install:

``` bash
pip install django
```

Create project:

``` bash
django-admin startproject myproject
```

Create app:

``` bash
python manage.py startapp users
```

Run server:

``` bash
python manage.py runserver
```

------------------------------------------------------------------------

# 4. Django Project Structure

    myproject

    ├── manage.py

    ├── settings.py

    ├── urls.py

    ├── models.py

    ├── views.py

    ├── templates

    └── static

------------------------------------------------------------------------

# 5. Django Models

Example:

``` python
from django.db import models

class Employee(models.Model):

    name = models.CharField(max_length=100)

    email = models.EmailField()

    created_at = models.DateTimeField(auto_now_add=True)
```

Migration:

``` bash
python manage.py makemigrations

python manage.py migrate
```

------------------------------------------------------------------------

# 6. Model Relationships

## One To One

``` python
class Profile(models.Model):

    user = models.OneToOneField(
        User,
        on_delete=models.CASCADE
    )
```

## Foreign Key

``` python
class Employee(models.Model):

    department = models.ForeignKey(
        Department,
        on_delete=models.CASCADE
    )
```

## Many To Many

``` python
class Student(models.Model):

    courses = models.ManyToManyField(
        Course
    )
```

------------------------------------------------------------------------

# 7. Django ORM Queries

Get all:

``` python
User.objects.all()
```

Filter:

``` python
User.objects.filter(
    active=True
)
```

Get single:

``` python
User.objects.get(id=1)
```

Create:

``` python
User.objects.create(
name="John"
)
```

Update:

``` python
User.objects.filter(
id=1
).update(
name="David"
)
```

Delete:

``` python
User.objects.filter(
id=1
).delete()
```

------------------------------------------------------------------------

# 8. Views

Function Based View:

``` python
from django.http import JsonResponse

def users(request):

    return JsonResponse({
        "message":"success"
    })
```

Class Based View:

``` python
from django.views import View

class UserView(View):

    def get(self,request):

        return JsonResponse({
            "status":"success"
        })
```

------------------------------------------------------------------------

# 9. URL Routing

Example:

``` python
from django.urls import path

urlpatterns = [

    path(
        "users/",
        users
    )

]
```

------------------------------------------------------------------------

# 10. Django Forms

Example:

``` python
from django import forms

class UserForm(forms.Form):

    name=forms.CharField()

    email=forms.EmailField()
```

------------------------------------------------------------------------

# 11. Authentication

Login:

``` python
from django.contrib.auth import authenticate

user = authenticate(
username="admin",
password="password"
)
```

Features:

-   Login
-   Logout
-   Password hashing
-   Permissions
-   Groups

------------------------------------------------------------------------

# 12. Middleware

Middleware processes requests and responses globally.

Example:

``` python
class CustomMiddleware:

    def __init__(self,get_response):

        self.get_response=get_response


    def __call__(self,request):

        response=self.get_response(request)

        return response
```

------------------------------------------------------------------------

# 13. Django REST Framework

Install:

``` bash
pip install djangorestframework
```

Serializer:

``` python
from rest_framework import serializers

class UserSerializer(serializers.ModelSerializer):

    class Meta:

        model = User

        fields="__all__"
```

API View:

``` python
from rest_framework.views import APIView
from rest_framework.response import Response

class UserAPI(APIView):

    def get(self,request):

        return Response({
            "message":"Success"
        })
```

------------------------------------------------------------------------

# 14. Authentication in DRF

Common methods:

-   JWT Authentication
-   Token Authentication
-   Session Authentication

JWT flow:

    Login

     |

    Generate Token

     |

    Client Stores Token

     |

    Send Token With API Request

     |

    Validate Token

------------------------------------------------------------------------

# 15. Query Optimization

select_related:

Used for ForeignKey and OneToOne.

``` python
Employee.objects.select_related(
"department"
)
```

prefetch_related:

Used for ManyToMany.

``` python
User.objects.prefetch_related(
"groups"
)
```

------------------------------------------------------------------------

# 16. Django Security

Important:

-   CSRF protection
-   XSS protection
-   SQL injection prevention
-   Secure cookies
-   Password hashing
-   HTTPS

------------------------------------------------------------------------

# 17. Django Signals

Example:

``` python
from django.db.models.signals import post_save

from django.dispatch import receiver


@receiver(post_save, sender=User)

def create_profile(sender,instance,created,**kwargs):

    if created:

        Profile.objects.create(
            user=instance
        )
```

------------------------------------------------------------------------

# 18. Caching

Options:

-   Redis
-   Database cache
-   Memory cache

Example:

``` python
from django.core.cache import cache

cache.set(
"user",
"John",
300
)
```

------------------------------------------------------------------------

# 19. Deployment

Production stack:

    Django

     |

    Gunicorn

     |

    Nginx

     |

    Server

Common tools:

-   Docker
-   AWS EC2
-   PostgreSQL
-   Redis

------------------------------------------------------------------------

# Scenario Based Interview Questions

## Q1. Django API is slow. How will you debug?

Answer:

Check:

-   Database queries
-   N+1 queries
-   Logs
-   Indexes

Solutions:

-   select_related
-   prefetch_related
-   caching

------------------------------------------------------------------------

## Q2. Migration conflict happened. What will you do?

Commands:

``` bash
python manage.py showmigrations

python manage.py makemigrations --merge
```

------------------------------------------------------------------------

## Q3. Difference between select_related and prefetch_related?

select_related:

-   SQL JOIN
-   ForeignKey
-   OneToOne

prefetch_related:

-   Multiple queries
-   ManyToMany

------------------------------------------------------------------------

## Q4. How do you secure Django APIs?

Answer:

-   Authentication
-   Permissions
-   CSRF protection
-   Input validation
-   HTTPS

------------------------------------------------------------------------

# Django Commands Cheat Sheet

``` bash
python manage.py runserver

python manage.py makemigrations

python manage.py migrate

python manage.py createsuperuser

python manage.py shell

python manage.py collectstatic

python manage.py test
```

------------------------------------------------------------------------

# 2 Years Experience Interview Checklist

Prepare:

-   Django MVT
-   Models
-   ORM
-   Views
-   URLs
-   Templates
-   Forms
-   Authentication
-   REST Framework
-   JWT
-   Middleware
-   Signals
-   Caching
-   Security
-   Deployment
-   Debugging scenarios
