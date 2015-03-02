# Base image to use, this must be set as the first line
FROM centos:6
MAINTAINER JianfuLi jianfu.li@outlook.com

# Install repos
RUN rpm -ivh http://mirror.overthewire.com.au/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm
RUN rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
RUN yum makecache
RUN yum update -y

RUN yum install -y openssh-server
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config

RUN echo 'root:123456' | chpasswd

# Start service
CMD /etc/init.d/sshd start && /bin/bash
