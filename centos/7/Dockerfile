FROM centos:7
MAINTAINER Alexandre Coilier "https://github.com/acoilier"

RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all

RUN yum install -y openssh-server &&\
    touch /run/utmp && \
    chmod u+s /usr/bin/ping
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa

RUN echo 'root:root' |chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
RUN mkdir /root/.ssh

RUN yum -y clean all && \
    rm -rf /tmp/* /var/tmp/*

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]