# Access A Postgres Database From The CLI

First you need to get the container ID or container name of your Postgres container.
```
$ docker ps
```

Once you have either, you need to enter the bash shell for that container.
```
$ docker exec -it <container-id/name> bash
```

From here you can run regular bash commands like `ls` or move through the directories in this container.

To access your databases, you need to log in as your postgres user; the default user is _probably_ `postgres`.
```
# psql -U <postgres-user>
```

From here, you can write your queries or [psql](https://github.com/jcatoe/til/blob/master/postgres/common-psql-commands.md) commands.
