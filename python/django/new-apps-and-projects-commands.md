# New Apps And Projects Commands

## Projects:

A project is the whole site you're building. Whatever name you give this project, will also be the name of the main folder that houses your `settings.py`.
```
django-admin startproject <project-name>
```

If you are already in the folder that you want to house your django project, you can avoid creating the original root folder by specifying the install location as "here" with `.`.

```
django-admin startproject <project-name> .
```

## Apps:

Apps help you group like code together like having a blog app and a forum app separated from each other instead of both of those apps using the same `views.py` or `models.py`.

```
python manage.py startapp <app-name>
```
