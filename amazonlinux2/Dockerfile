FROM amazonlinux:2
LABEL maintainer="buluma"
LABEL build_date="2024-03-25"

ENV container=docker

ENV pip_packages "ansible"

# Install systemd -- See https://hub.docker.com/_/centos/
RUN yum -y update; yum clean all

# Install requirements. # TODO https://github.com/robertdebock/docker-amazonlinux-systemd/blob/master/Dockerfile
RUN yum makecache fast \
 && yum -y install deltarpm epel-release initscripts systemd \
 && yum -y update \
 && yum -y install \
      sudo \
      which \
      python-pip \
 && yum clean all

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
