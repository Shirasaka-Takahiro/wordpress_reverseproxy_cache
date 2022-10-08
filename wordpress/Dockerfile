FROM centos:7
RUN yum -y install httpd wget \
    && yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm \
    && yum -y install php php-mbstring php-xml php-xmlrpc php-gd php-pdo php-pecl-mcrypt php-mysqlnd php-pecl-mysql --enablerepo=remi-php74 \
    && mkdir -p /var/www/vhosts/onya-lab.site/public_html \
    && touch /etc/httpd/conf.d/onya-lab.site.conf \
    && yum clean all
COPY ./httpd/onya-lab.site.conf /etc/httpd/conf.d/onya-lab.site.conf
WORKDIR /var/www/vhosts/onya-lab.site
RUN wget https://ja.wordpress.org/latest-ja.tar.gz \
    && tar -zxvf latest-ja.tar.gz \
    && mv /var/www/vhosts/onya-lab.site/wordpress/* /var/www/vhosts/onya-lab.site/public_html/ \
    && cp -ip /var/www/vhosts/onya-lab.site/public_html/wp-config-sample.php /var/www/vhosts/onya-lab.site/public_html/wp-config.php \
    && chown -R apache:apache /var/www/vhosts/onya-lab.site
COPY ./wp-config.php /var/www/vhosts/onya-lab.site/public_html/wp-config.php
EXPOSE 8080
ENTRYPOINT ["/usr/sbin/httpd", "-DFOREGROUND"]