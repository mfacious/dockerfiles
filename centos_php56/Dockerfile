# Base image to use, this must be set as the first line
FROM centos:base
MAINTAINER JianfuLi lijianfu@outlook.com

# Install nginx
RUN yum install -y nginx

# Install php
RUN yum install -y php php-cli php-devel php-fpm php-imap php-ioncube-loader php-ldap php-mbstring php-mcrypt php-odbc php-opcache php-pdo php-pecl-amqp php-pecl-apcu php-pecl-crypto php-pecl-dio php-pecl-eio php-pecl-ev php-pecl-event php-pecl-gearman php-pecl-http php-pecl-igbinary php-pecl-imagick php-pecl-jsonc php-pecl-memcache php-pecl-memcached php-pecl-memprof php-pecl-mongo php-pecl-redis php-pecl-xhprof php-pecl-yaf php-xml php-mysql php-phalcon --enablerepo=remi,remi-php56
# Config timezone
RUN sed -ri 's/date.timezone =/date.timezone = \"Asia\/Shanghai\"/g' /etc/php.ini

# Config nginx 
RUN rm -rf /etc/nginx/nginx.conf
ADD ./nginx.conf /etc/nginx/nginx.conf
# Config nginx pool
RUN rm -rf /etc/nginx/conf.d/*.conf
ADD ./default.conf /etc/nginx/conf.d/default.conf
# Config php pool
RUN rm -rf /etc/php-fpm.d/www.conf
ADD ./www.conf /etc/php-fpm.d/www.conf

# Expose web port
EXPOSE 80

# Env
ENV ENVIRONMENT DEVELOPMENT

# Start service
CMD service nginx start && service php-fpm start && /usr/bin/wc 