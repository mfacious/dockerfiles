FROM centos:sshd
MAINTAINER JianfuLi jianfu.li@outlook.com

# Install mysql
RUN rpm -ivh http://dev.mysql.com/get/mysql-community-release-el6-5.noarch.rpm
RUN yum install -y mysql-community-server mysql-community-client

# Init mysql password
RUN /etc/init.d/mysqld start && /usr/bin/mysqladmin -u root password '123456'

# Expose mysql port
EXPOSE 3306

# Start service
CMD /etc/init.d/sshd start && /etc/init.d/mysqld start && /bin/bash
