FROM antpolis/base-machine
MAINTAINER Chris Sim <chris.sim@antpolis.com>
ADD deps/apache/development.conf /etc/apache2/sites-available/development.conf
ENV DEVFOLDER /var/www/development

RUN mkdir $DEVFOLDER
RUN a2ensite development

COPY deps/start_safe_perms /usr/bin/
RUN chmod +x /usr/bin/start_safe_perms

WORKDIR $DEVFOLDER

EXPOSE 80

CMD ["start_safe_perms", "-D FOREGROUND"]
