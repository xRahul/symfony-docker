comment out the line--
```yml
            - ./logs/symfony:/var/www/symfony/app/logs
```
before creating the symfony project

now run the 
```sh
docker-compose up --build
```

####To create the symfony project for the first time

After all three servers are running, open tty to the php
```sh
docker exec -it >>>PHP_SERVER<<< /bin/bash
```
then get into `/var/www` and run--
```sh
composer create-project symfony/framework-standard-edition symfony "2.8.*" -vvv
```

and exit out

Also create a `symfony.dev` entry in `/etc/hosts` pointing to `localhost` or `127.0.0.1` on your host system
