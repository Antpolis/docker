FROM antpolis/base-nodejs-machine
MAINTAINER Chris Sim <chris.sim@antpolis.com>

## Setting up ENV
ENV PHANTOM_JS phantomjs-1.9.8-linux-i686.tar.bz2

## Setting up server
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Asia/Singapore /etc/localtime
RUN mkdir -p /tmp/installation
RUN mkdir -p /opt/drivers

ADD deps/chromedriver /opt/drivers/chromedriver
ADD deps/selenium-server-standalone.jar /usr/local/share/selenium-server-standalone.jar
COPY deps/$PHANTOM_JS /tmp/installation/$PHANTOM_JS
WORKDIR /tmp/installation

## Installing
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
RUN apt-get update -y && apt-get install -y wget python-pip xvfb google-chrome-stable build-essential \
  chrpath libssl-dev libxft-dev libfreetype6 libfreetype6-dev libfontconfig1 libfontconfig1-dev \
  openjdk-7-jdk
RUN tar xvjf $PHANTOM_JS


RUN mv $PHANTOM_JS /usr/local/share/phantomjs-1.9
RUN ln -sf /usr/local/share/phantomjs-1.9/bin/phantomjs /usr/local/bin

RUN pip install pyvirtualdisplay selenium
RUN npm install -g mocha nightwatch

RUN rm -rf /tmp/installation
