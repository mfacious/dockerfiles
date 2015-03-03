# Base image to use, this must be set as the first line
FROM centos:6
MAINTAINER JianfuLi jianfu.li@outlook.com

# Install repos
RUN rpm -ivh http://mirror.overthewire.com.au/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -ivh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm
RUN yum makecache
RUN yum update -y

# Start service
CMD /bin/bash
