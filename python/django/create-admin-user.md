If working within Docker, you will need to enter the container's Bash interface.
```
$ docker exec -it <container_name_or_id> bash
```

Make sure you've run your migrations at least once to create the `admin` and `auth` tables.
```
$ python manage.py migrate
```

Launch Django `createsuperuser` function:
```
$ python manage.py createsuperuser
```

You will then have the options to set a username (leave blank for `root`), email address, and password for the admin user.

To test that your user was created, you can try accessing the admin page of your Django site > http://127.0.0.1:8000/admin.
You should be able to access the site administration page and see at least two tables: `Groups` and `Users`
