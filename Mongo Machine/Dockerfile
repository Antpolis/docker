FROM tutum/mongodb:latest
MAINTAINER Chris Sim <chris.sim@antpolis.com>

RUN service apache2 restart
CMD ["start_safe_perms", "-D FOREGROUND"]
