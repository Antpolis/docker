FROM antpolis/php-development-machine
MAINTAINER Chris Sim <chris.sim@antpolis.com>
ADD deps/apache/development.conf /etc/apache2/sites-available/development.conf
ENV DEVFOLDER /var/www/html

RUN mkdir $DEVFOLDER
RUN a2ensite development

WORKDIR $DEVFOLDER

EXPOSE 9002

CMD ["start_safe_perms", "-D FOREGROUND"]
