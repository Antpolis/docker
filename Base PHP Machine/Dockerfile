FROM ubuntu:14.04
MAINTAINER Chris Sim <chris.sim@antpolis.com>
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install apache2 mysql-server libapache2-mod-auth-mysql \
								php5-mysql php5 libapache2-mod-php5 php5-mcrypt php5-common \
								php5-curl php5-gd php5-cli php5-cgi php5-tidy git wget curl
RUN apt-get clean

RUN php5enmod mcrypt
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/bin/composer
RUN chmod +x /usr/bin/composer

RUN composer global require "fxp/composer-asset-plugin:~1.1.1"

COPY deps/composer/auth.json ~/.composer

COPY deps/start_safe_perms /usr/local/bin/
COPY deps/correct_user /usr/local/bin/
RUN chmod +x /usr/local/bin/start_safe_perms
RUN chmod +x /usr/local/bin/correct_user

COPY  ./deps/mysql/my.cnf /etc/mysql/my.cnf

RUN chown -Rf www-data:www-data /var/www
RUN chmod -Rf 775 /var/www

EXPOSE 80 3306

CMD service apache2 restart
