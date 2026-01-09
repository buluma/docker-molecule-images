# syntax=docker/dockerfile:1
FROM almalinux:10

LABEL maintainer="Michael Buluma <me@buluma.me.ke>"
LABEL build_date="2026-01-09"

LABEL org.opencontainers.image.title="Docker AlmaLinux 10 Systemd" \
      org.opencontainers.image.description="AlmaLinux 10 Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker
ENV DEBIAN_FRONTEND noninteractive

# Enable systemd.
RUN dnf -y install systemd systemd-sysv && \
    dnf clean all && \
    rm -rf /var/cache/dnf && \
    rm -rf /lib/systemd/system/multi-user.target.wants/* && \
    rm -rf /etc/systemd/system/*.wants/* && \
    rm -rf /lib/systemd/system/local-fs.target.wants/* && \
    rm -rf /lib/systemd/system/sockets.target.wants/*udev* && \
    rm -rf /lib/systemd/system/sockets.target.wants/*initctl* && \
    rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* && \
    rm -rf /lib/systemd/system/systemd-update-utmp*

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/lib/systemd/systemd"]