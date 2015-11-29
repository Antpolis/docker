FROM antpolis/development-machine
ADD deps/apache/development.conf /etc/apache2/sites-available/development.conf
RUN mkdir /var/www/development
RUN a2ensite development
EXPOSE 80

CMD exec /usr/sbin/apachectl -D FOREGROUND
