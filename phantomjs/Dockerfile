# dockerhub - A repository for various dockerfiles
# For more information; http://github.com/cmfatih/dockerhub
#
# phantomjs
#
# Usage
#   docker run cmfatih/phantomjs /usr/bin/phantomjs -v
#   docker run cmfatih/phantomjs /usr/bin/casperjs --version
#   docker run -v `pwd`:/mnt/test cmfatih/phantomjs /usr/bin/phantomjs /mnt/test/test.js

# VERSION 1.0.1

FROM ubuntu:14.04

MAINTAINER Chris Sim<chris.sim@antpolis.com>

# Env
ENV PHANTOMJS_VERSION 1.9.8


RUN apt-get update -y

RUN apt-get install -y build-essential g++ flex bison gperf ruby perl \
  libsqlite3-dev libfontconfig1-dev libicu-dev libfreetype6 libssl-dev \
  libpng-dev libjpeg-dev python libx11-dev libxext-dev wget

WORKDIR /tmp

RUN wget -q --no-check-certificate https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.8-linux-x86_64.tar.bz2
RUN tar -xvf phantomjs-1.9.8-linux-x86_64.tar.bz2

RUN mv phantomjs-1.9.8-linux-x86_64/bin/phantomjs /usr/bin/phantomjs

EXPOSE 4444

# Default command