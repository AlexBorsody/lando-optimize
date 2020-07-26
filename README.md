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


# Troubleshooting

If `lando rebuild` `lando restart` or `lando composer install` doesn't help try deleting your /core and /vendor folder and running `lando install` or `lando composer install`.

More info below.

https://github.com/geerlingguy/drupal-vm/issues/1439

https://github.com/drupal-composer/drupal-packagist/issues/66

