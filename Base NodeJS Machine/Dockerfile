FROM node:5.1.0-wheezy
MAINTAINER Chris Sim <chris.sim@antpolis.com>

RUN apt-get update && apt-get upgrade -y && apt-get install -y build-essential libssl-dev nginx python wget git

RUN npm install -g sails bower pm2 grunt
