FROM centos:6
MAINTAINER Rahul Jain <rahul.jain@shopclues.com>


RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm && \
    rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm && \
    yum update -y && \
    yum upgrade -y && \
    yum install -y --enablerepo=remi php-common php-cli php-fpm php-mcrypt php-pecl-apc php-gd php-intl php-xml php-mbstring php-process php-pdo php-peck-xdebug php php-dom curl php-curl openssl openssl-devel php-bcmath php-devel php-mysql php-odbc php-pdo php-pear php-pecl-apcu php-pecl-igbinary php-pecl-memcache php-pecl-memcached php-pecl-mongo php-pecl-msgpack php-pecl-redis php-pecl-solr php-pecl-sqlite php-phalcon php-soap

ADD symfony.ini /etc/php-fpm.d/
ADD symfony.ini /etc/php.d/

RUN rm /etc/php-fpm.d/www.conf
ADD symfony.pool.conf /etc/php-fpm.d/

####composer to install symfony2.8
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '55d6ead61b29c7bdee5cccfb50076874187bd9f21f65d8991d46ec5cc90518f447387fb9f76ebae1fbbacf329e583e30') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer
WORKDIR /var/www/
#RUN composer create-project symfony/framework-standard-edition symfony "2.8.*" -vvv

RUN usermod -u 1000 apache

CMD ["php-fpm", "-F"]

EXPOSE 9000
