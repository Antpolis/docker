FROM ubuntu:14.04

RUN apt-get -y update
RUN apt-get -y install apache2 mysql-server libapache2-mod-auth-mysql \
								php5-mysql php5 libapache2-mod-php5 php5-mcrypt php5-common \
								php5-curl php5-gd php5-cli php5-cgi php5-tidy

EXPOSE 3306 80

CMD service apache2 restart
