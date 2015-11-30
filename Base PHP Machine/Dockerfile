FROM ubuntu:14.04
MAINTAINER Chris Sim <chris.sim@antpolis.com>
RUN apt-get -y update
RUN apt-get -y install apache2 mysql-server libapache2-mod-auth-mysql \
								php5-mysql php5 libapache2-mod-php5 php5-mcrypt php5-common \
								php5-curl php5-gd php5-cli php5-cgi php5-tidy git wget

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

EXPOSE 3306 80

RUN php5enmod mcrypt

COPY  ./deps/mysql/my.cnf /etc/mysql/my.cnf

CMD service apache2 restart
