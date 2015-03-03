FROM centos:base
MAINTAINER JianfuLi jianfu.li@outlook.com

RUN yum install -y openssh-server
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config

RUN echo 'root:123456' | chpasswd

# Expose sshd port
EXPOSE 22

# Start service
CMD /etc/init.d/sshd start && /bin/bash
