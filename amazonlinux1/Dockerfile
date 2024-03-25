FROM amazonlinux:1

LABEL maintainer="buluma"
LABEL build_date="2024-03-24"

ENV container=docker

RUN yum -y install upstart

VOLUME ["/sys/fs/cgroup"]
CMD ["/sbin/init"]
