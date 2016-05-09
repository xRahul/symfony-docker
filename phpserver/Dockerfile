FROM centos:6

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
RUN rpm -Uvh https://mirror.webtatic.com/yum/el6/latest.rpm

RUN yum -y update

RUN yum -y install php54w-common php54w-cli php54w-fpm php54w-mcrypt php54w-mysql php54w-pecl-apc php54w-gd php54w-intl php54w-xml php54w-mbstring php54w-process php54w-pdo php54w-pecl-xdebug 

ADD symfony.ini /etc/php-fpm.d/
ADD symfony.ini /etc/php.d/

RUN rm /etc/php-fpm.d/www.conf
ADD symfony.pool.conf /etc/php-fpm.d/

####composer to install symfony2.8
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '92102166af5abdb03f49ce52a40591073a7b859a86e8ff13338cf7db58a19f7844fbc0bb79b2773bf30791e935dbd938') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer
WORKDIR /var/www/
#RUN composer create-project symfony/framework-standard-edition symfony "2.8.*" -vvv

RUN usermod -u 1000 apache

CMD ["php-fpm", "-F"]

EXPOSE 9000
