# syntax=docker/dockerfile:1
FROM opensuse/leap:15.6

LABEL maintainer="Michael Buluma <bulumaknight@gmail.com>"
LABEL build_date="2026-07-11"

LABEL org.opencontainers.image.title="openSUSE Leap 15.6 Systemd" \
      org.opencontainers.image.description="openSUSE Leap 15.6 Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker

RUN zypper refresh && \
    zypper install -y dbus-1 systemd-sysvinit sudo && \
    zypper clean -a && \
    rm -rf /tmp/* /var/tmp/* /usr/share/doc/packages/* && \
    cd /usr/lib/systemd/system/sysinit.target.wants/; \
    for i in *; do [ $i = systemd-tmpfiles-setup.service ] || rm -f $i; done; \
    rm -f /usr/lib/systemd/system/multi-user.target.wants/*; \
    rm -f /etc/systemd/system/*.wants/*; \
    rm -f /usr/lib/systemd/system/local-fs.target.wants/*; \
    rm -f /usr/lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /usr/lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /usr/lib/systemd/system/basic.target.wants/*; \
    rm -f /usr/lib/systemd/system/anaconda.target.wants/*

VOLUME ["/sys/fs/cgroup"]

CMD ["/sbin/init"]