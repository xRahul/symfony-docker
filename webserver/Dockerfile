FROM centos:8

RUN yum -y install epel-release
RUN yum -y update

RUN yum -y install nginx

RUN mkdir /etc/nginx/sites-available
RUN mkdir /etc/nginx/sites-enabled

ADD nginx.conf /etc/nginx/
ADD symfony.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/symfony

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 nginx

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
