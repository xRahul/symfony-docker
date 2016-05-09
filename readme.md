comment out the line--
            - ./logs/symfony:/var/www/symfony/app/logs
before creating the symfony project

run the docker-compose up

docker exec -it >>>PHP_SERVER<<< /bin/bash

in /var/www-->>
composer create-project symfony/framework-standard-edition symfony "2.8.*" -vvv

exit



