# syntax=docker/dockerfile:1
FROM opensuse/leap:16.0

LABEL maintainer="Michael Buluma <bulumaknight@gmail.com>"
LABEL build_date="2026-07-11"

LABEL org.opencontainers.image.title="openSUSE Leap 16.0 Systemd" \
      org.opencontainers.image.description="openSUSE Leap 16.0 Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker

RUN zypper refresh && \
    zypper install -y systemd sudo && \
    zypper clean -a && \
    rm -rf /var/cache/zypp && \
    rm -rf /lib/systemd/system/multi-user.target.wants/* && \
    rm -rf /etc/systemd/system/*.wants/* && \
    rm -rf /lib/systemd/system/local-fs.target.wants/* && \
    rm -rf /lib/systemd/system/sockets.target.wants/*udev* && \
    rm -rf /lib/systemd/system/sockets.target.wants/*initctl* && \
    rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* && \
    rm -rf /lib/systemd/system/systemd-update-utmp*

VOLUME ["/sys/fs/cgroup"]

CMD ["/lib/systemd/systemd"]
