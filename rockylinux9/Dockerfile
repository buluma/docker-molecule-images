FROM rockylinux:9
LABEL maintainer="Michael Buluma"
LABEL build_date="2024-03-25"

ENV container=docker

ENV pip_packages "ansible"

# Install systemd -- See https://hub.docker.com/_/centos/
RUN rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

# Upgrade packages.
RUN yum -y update \
&& yum clean all

# Install pip
RUN yum -y install python3-pip python3-setuptools python3-wheel

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
