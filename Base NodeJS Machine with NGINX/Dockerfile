FROM antpolis/base-nodejs-machine
MAINTAINER Chris Sim <chris.sim@antpolis.com>

RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install nginx
RUN apt-get clean

COPY ./deps/nginx/default.conf /etc/nginx/sites-avaiable/default.conf

EXPOSE 80
