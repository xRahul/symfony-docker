FROM centos:6

RUN yum -y install epel-release
RUN yum -y update

RUN yum -y install php php-common php-cli php-fpm php-mcrypt php-mysql php-apcu php-gd php-curl php-intl php-pecl-imagick 

ADD symfony.ini /etc/php-fpm.d/
ADD symfony.ini /etc/php.d/

ADD symfony.pool.conf /etc/php-fpm.d/

RUN usermod -u 1000 apache

CMD ["php5-fpm", "-F"]

EXPOSE 9000
