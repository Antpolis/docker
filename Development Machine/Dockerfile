FROM antpolis/development-machine
ADD deps/apache/development.conf /etc/apache2/sites-available/development.conf

RUN a2ensite development
EXPOSE 80

CMD service apache2 restart
