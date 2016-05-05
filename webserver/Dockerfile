FROM centos:6

RUN yum -y install epel-release
RUN yum -y update

RUN yum -y install nginx

ADD nginx.conf /etc/nginx/
