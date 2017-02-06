FROM antpolis/nodejs-machine

RUN mkdir -p /tmp/testing-container
WORKDIR /tmp/testing-container

RUN npm install -g nightwatch codeceptjs webdriverio protractor selenium-webdriver

RUN apt-get update && apt-get install -y default-jdk

WORKDIR /opt

COPY deps/selenium-server-standalone-2.53.0.jar ./

RUN ln -s /opt/selenium-server-standalone-2.53.0.jar /usr/bin/selenium

RUN mkdir -p /var/www/html

WORKDIR /var/www/html

VOLUME /var/www/html
