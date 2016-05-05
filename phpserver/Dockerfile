FROM centos:6

RUN yum -y install epel-release
RUN yum -y update

RUN yum -y install php php-common php-cli php-fpm php-mcrypt php-mysql php-apcu php-gd php-curl php-intl php-pecl-imagick 

RUN yum -y install php-xml

ADD symfony.ini /etc/php-fpm.d/
ADD symfony.ini /etc/php.d/

RUN rm /etc/php-fpm.d/www.conf
ADD symfony.pool.conf /etc/php-fpm.d/

RUN usermod -u 1000 apache

CMD ["php-fpm", "-F"]

EXPOSE 9000
