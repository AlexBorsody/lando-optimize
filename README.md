# lando_mysql_stop_connecting
A solution for mysql stop connecting after `lando restart` https://github.com/lando/lando/issues/1718

I think I found a solution, 
I had same issue multiple times, and I was forced to completely uninstall my application and  install it again, which resulted in recreating the database. This time I took my time and try to solve this *** problem.

This script has all the commands, so just take and execute it.

So first I've shut lando

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

Optimize Docker

```
docker system prune
```

This prevents you from resorting to a `lando destroy` and blowing away your database.

```
lando poweroff
$ lando --clear
$ docker rm -f $(docker ps --filter label=io.lando.container=TRUE --all -q)
# then i restart docker manually
```



