FROM debian:jessie
MAINTAINER Diego Najar

# Variables
ENV NGINX_VERSION 1.10.2-1~jessie
ENV nginx_conf /etc/nginx/nginx.conf
ENV php_conf /etc/php5/fpm/php.ini
ENV fpm_conf /etc/php5/fpm/php-fpm.conf
ENV fpm_pool /etc/php5/fpm/pool.d/www.conf

# Packages installation
RUN apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62 && \
	echo "deb http://nginx.org/packages/debian/ jessie nginx" >> /etc/apt/sources.list && \
	apt-get update && \
	apt-get install --no-install-recommends --no-install-suggests -y \
						ca-certificates \
						nginx=${NGINX_VERSION} \
						nginx-module-xslt \
						nginx-module-geoip \
						nginx-module-image-filter \
						nginx-module-perl \
						nginx-module-njs \
						gettext-base \
						php5-fpm \
						supervisor

# Needed package
RUN apt-get install --no-install-recommends --no-install-suggests -y php5-mysql php5-mcrypt php5-common php5-curl php5-gd php5-cli php5-cgi php5-tidy git wget curl

RUN php5enmod mcrypt
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/bin/composer
RUN chmod +x /usr/bin/composer

RUN composer global require "fxp/composer-asset-plugin:~1.1.1"

# Hacks Nginx and php-fpm config
RUN sed -i -e "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g" ${php_conf} && \
	sed -i -e "s/upload_max_filesize\s*=\s*2M/upload_max_filesize = 100M/g" ${php_conf} && \
	sed -i -e "s/post_max_size\s*=\s*8M/post_max_size = 100M/g" ${php_conf} && \
	sed -i -e "s/variables_order = \"GPCS\"/variables_order = \"EGPCS\"/g" ${php_conf} && \
	sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" ${fpm_conf} && \
	sed -i -e "s/listen = 127.0.0.1:9000/listen = \/var\/run\/php-fpm.sock/g" ${fpm_pool} && \
	sed -i -e "s/listen.owner = www-data/listen.owner = nginx/g" ${fpm_pool} && \
	sed -i -e "s/listen.group = www-data/listen.group = nginx/g" ${fpm_pool} && \
	sed -i -e "s/user = www-data/user = nginx/g" ${fpm_pool} && \
	sed -i -e "s/group = www-data/group = nginx/g" ${fpm_pool} && \
	echo "daemon off;" >> ${nginx_conf}

# Cleaning
RUN rm -rf /etc/nginx/conf.d/* && \
    rm -rf /usr/share/nginx/html/* && \
	rm -rf /var/lib/apt/lists/*

# Configurations files
ADD conf/default.conf /etc/nginx/conf.d/default.conf
ADD conf/supervisord.conf /etc/supervisord.conf
ADD www/index.php /usr/share/nginx/html/index.php

# Nginx logs to Docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
	ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80 443

CMD ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]
