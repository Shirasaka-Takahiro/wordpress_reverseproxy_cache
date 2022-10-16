FROM phpmyadmin/phpmyadmin
ENV PMA_ARBITRARY=1
ENV PMA_HOSTS=db
ENV PMA_USER=wp_user
ENV PMA_PASSWORD=Wordpress1!
ENV VIRTUAL_HOST=pma.onya-lab.site
COPY ./000-default.conf /etc/apache2/sites-enabled/000-default.conf