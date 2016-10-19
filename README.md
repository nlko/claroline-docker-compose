# Requirements

Having *docker-compose* installed on your machine.


# starting the machine

```
docker-compose up -d
```

# stoping the machines

`docker-compose down`

# Accessing machines

`docker-compose run [web|db] bash`

## Example usage - install Claroline Connect verison 16.05 via traball
```
docker-compose run web "curl packages.claroline.net/releases/latest/claroline-16.05.tar.gz | tar xzv --strip 1"

docker-compose run web "chmod -R 777 app/cache app/config app/logs app/sessions files web"
```

## Example usage - install latest Claroline Connect master via git
```
docker-compose run web git clone http://github.com/claroline/Claroline .
docker-compose run web php scripts/configure.php
docker-compose run web composer sync-dev
docker-compose run web chmod -R 777 app/cache app/config app/logs app/sessions files web
docker-compose run web php app/console claroline:user:create
```

## Example files backup :
```
docker run -v clarolinedockercompose_data:/data -v /dockerbackup/claroline:/backup busybox tar -czf /backup/backup.tar.gz /data/
```


git clone http://github.com/nlko/Claroline-dev claroline
git clone http://github.com/nlko/Distribution-dev distribution
docker-compose up -d
docker-compose exec web php scripts/configure.php
docker-compose exec web composer sync-dev
docker-compose exec web chmod -R 777 app/cache app/config app/logs app/sessions files web
docker-compose exec web php app/console claroline:user:create -a


pp/console claroline:user:create -a
app/console assets:install --symlink
app/console assetic:dump
