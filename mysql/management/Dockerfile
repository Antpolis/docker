FROM ubuntu:16.04

RUN apt-get -y update && apt-get install -y wget libaio1

WORKDIR tmp

RUN wget http://dev.mysql.com/get/Downloads/MySQL-Cluster-7.5/mysql-cluster-gpl-7.5.4-debian8-x86_64.deb

RUN dpkg -i mysql-cluster-gpl-7.5.4-debian8-x86_64.deb

RUN mkdir -p /var/lib/mysql-cluster

COPY config.ini /var/lib/mysql-cluster