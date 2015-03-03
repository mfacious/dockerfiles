# Base image to use, this must be set as the first line
FROM centos:sshd
MAINTAINER JianfuLi jianfu.li@outlook.com

# Install nginx
RUN rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm
RUN yum install -y nginx

# Install php
RUN rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
RUN yum install -y php php-cli php-devel php-fpm php-imap php-ioncube-loader php-ldap php-mbstring php-mcrypt php-odbc php-opcache php-pdo php-pecl-amqp php-pecl-apcu php-pecl-crypto php-pecl-dio php-pecl-eio php-pecl-ev php-pecl-event php-pecl-gearman php-pecl-http php-pecl-igbinary php-pecl-imagick php-pecl-jsonc php-pecl-memcache php-pecl-memcached php-pecl-memprof php-pecl-mongo php-pecl-redis php-pecl-xhprof php-pecl-yaf php-xml php-mysql php-phalcon --enablerepo=remi,remi-php56

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
CMD service nginx start && service php-fpm start && /bin/bash 
