docker pull centos:6

sudo cp /etc/php.ini.default /etc/php.ini
sudo vim /etc/php.ini
date.timezone = "Asia/Kolkata"
php --ini

composer create-project symfony/framework-standard-edition app "2.8.*" -vvv
cd app/
php app/console cache:clear



