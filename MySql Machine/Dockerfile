FROM ubuntu:14.04
MAINTAINER Chris Sim <chris.sim@antpolis.com>
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install mysql-server

RUN apt-get clean

COPY  ./deps/mysql/my.cnf /etc/mysql/my.cnf

RUN /usr/sbin/mysqld & \
    sleep 10s &&\
    echo "GRANT ALL ON *.* TO admin@'%' IDENTIFIED BY 'shohoku10' WITH GRANT OPTION; FLUSH PRIVILEGES" | mysql

EXPOSE 3306

ENTRYPOINT '/usr/bin/mysqld_safe'

CMD start
