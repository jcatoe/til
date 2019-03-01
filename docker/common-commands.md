# Common Docker CLI Commands

## Containers:

Note: `docker ps` only shows _running_ containers and the flag `-a` forces the command to show all of the containers.

More [reading](https://docs.docker.com/engine/reference/commandline/ps/) on the old syntax with `ps`.

### List:
New syntax:
```
$ docker container ls
```

Old syntax:
```
$ docker ps -a
```

### Delete all:
**Warning:** this will _destroy_ your containers and you _will not_ be able to get them back.
```
$ docker rm $(docker ps -a -q)
```


## Images:

### Delete all:
**Warning:** this will _destroy_ your images and you _will not_ be able to get them back.
```
$ docker rmi $(docker images -q)
```

## Volumes:

### List:
```
$ docker volume ls
```
