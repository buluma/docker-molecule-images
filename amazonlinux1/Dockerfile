# syntax=docker/dockerfile:1
FROM amazonlinux:1

LABEL maintainer="buluma"
LABEL build_date="2024-03-27"

LABEL org.opencontainers.image.title="Docker Ubuntu Noble Systemd" \
      org.opencontainers.image.description="Ubuntu Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker

RUN yum -y install upstart

VOLUME ["/sys/fs/cgroup"]
CMD ["/sbin/init"]
