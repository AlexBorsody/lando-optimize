# Lando cure all
shut down

```shell
$ lando stop
$ lando poweroff
```

and after that I cleared lando

```shell
$ lando --clear
```
then clear all docker containers (you could simply clear the container you want)

stop all containers:

```shell
$ docker kill $(docker ps -q)
```

remove all containers
```shell
$ docker rm $(docker ps -a -q)
```

remove all docker images

```shell
$ docker rmi $(docker images -q)
```

after that I went to my application directory and started it up

```shell
$ lando start
```

And try running 

```shell
$ lando mysql -v
```

to check your database or 

```shell
$ docker ps
```

# Optimize Docker

Optimize and keep database

```
$ docker system prune
```

This prevents you from resorting to a `lando destroy` and blowing away your database

```
$ lando poweroff
$ lando --clear
$ docker rm -f $(docker ps --filter label=io.lando.container=TRUE --all -q)
# then restart docker manually
```



