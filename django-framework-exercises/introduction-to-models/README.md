# Introduction to Django Models

## Overview
Models are the single, definitive source of information about your data. They contain the essential fields and behaviors of the data you’re storing. Generally, each model maps to a single database table.

## Tasks
1. In your `myapp` app, open `models.py`.
2. Create a model class named `Post`.
3. Add the following fields:
    * `title`: A `CharField` with a maximum length of 200.
    * `content`: A `TextField`.
    * `created_at`: A `DateTimeField` that is automatically set to the current date/time when the object is created.
4. Add a `__str__` method to return the title of the post.
5. Register your model in `admin.py` so you can see it in the Django Admin interface.

### Example `models.py`:
```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```

### Example `admin.py`:
```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

## Migrations
After creating or modifying a model, you must create and apply migrations:
1. Run `python manage.py makemigrations` to package your changes.
2. Run `python manage.py migrate` to apply them to the database.

## Verification
1. Create a superuser: `python manage.py createsuperuser`.
2. Run the server: `python manage.py runserver`.
3. Go to `http://127.0.0.1:8000/admin/`, log in, and check if you can add a new Post.

## Input/Output:
```
A working database model registered in the Django Admin.
```
