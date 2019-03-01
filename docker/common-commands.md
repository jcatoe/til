# Common Docker CLI Commands

NOTE ON SYNTAX CHANGE

## Containers:

### List:

List running containers:
```
$ docker container ls
```

List all containers:
```
$ docker container ls --all
```

List only the ids:
```
$ docker container ls -aq
```
* `-a` for all
* `-q` for quiet mode

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
