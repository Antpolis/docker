FROM ubuntu:16.04
MAINTAINER Chris Sim


RUN apt-get -y update && apt-get install -y python-software-properties software-properties-common && apt-get update && apt-get -qq upgrade
RUN add-apt-repository -y ppa:pinepain/libv8-5.2 && apt-get update


RUN apt-get install -y \
  build-essential \
  imagemagick \
  libpcre3 \
  php7.0 \
  php7.0-cli \
  php7.0-dev \
  php7.0-bcmath \
  php7.0-bz2 \
  php7.0-mysql \
  php7.0-mbstring \
  php7.0-mcrypt \
  php7.0-gd \
  php-imagick \
  php7.0-curl \
  php7.0-intl \
  php7.0-common \
  php7.0-json \
  php7.0-opcache \
  php7.0-recode \
  php7.0-soap \
  php7.0-xml \
  php7.0-zip \
  php7.0-opcache \
  php-apcu \
  php-gettext \
  git \
  rsyslog \
  curl  \
  wget \
  nano \
  libv8-dev

RUN curl https://getcomposer.org/installer | php -- && mv composer.phar /usr/local/bin/composer && chmod +x /usr/local/bin/composer

RUN printf "\n" | pecl install -f -a -l v8js-1.3.3

RUN echo "extension=v8js.so" >> /etc/php/7.0/fpm/conf.d/v8js.ini

RUN apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 9000

COPY www.conf /etc/php/7.0/fpm/pool.d/www.conf

RUN mkdir /run/php

WORKDIR /var/www/html
VOLUME /var/www/html
ENTRYPOINT  ["/usr/sbin/php-fpm7.0"]
CMD ["-F"]
