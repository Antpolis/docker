FROM antpolis/php-development-machine
MAINTAINER Chris Sim <chris.sim@antpolis.com>
ADD deps/apache/development.conf /etc/apache2/sites-available/development.conf
ENV DEVFOLDER /var/www/development

RUN apt-get update && apt-get install -y nodejs npm

RUN ln -s /usr/bin/nodejs /usr/bin/node

RUN npm install bower -g

RUN mkdir $DEVFOLDER
RUN a2ensite development

WORKDIR $DEVFOLDER

EXPOSE 80

CMD ["start_safe_perms", "-D FOREGROUND"]
