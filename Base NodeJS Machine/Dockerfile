FROM node:6.2.2-wheezy
MAINTAINER Chris Sim <chris.sim@antpolis.com>

RUN apt-get update && apt-get upgrade -y && apt-get install -y build-essential libssl-dev nginx python wget git

RUN npm install -g sails bower pm2 grunt-cli coffeelint gulp-cli

RUN npm cache clean

RUN git config --global url."https://".insteadOf git://


VOLUME /var/www/html

WORKDIR /var/www/html