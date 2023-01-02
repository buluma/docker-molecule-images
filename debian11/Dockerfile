FROM debian:bullseye

LABEL maintainer="buluma"
LABEL build_update="2023-01-02"

ARG DEBIAN_FRONTEND=noninteractive

ENV container docker

# Enable systemd.
RUN apt-get update ; \
    apt-get install -y systemd systemd-sysv ; \
    apt-get clean ; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* ; \
    rm -rf /lib/systemd/system/multi-user.target.wants/* ; \
    rm -rf /etc/systemd/system/*.wants/* ; \
    rm -rf /lib/systemd/system/local-fs.target.wants/* ; \
    rm -rf /lib/systemd/system/sockets.target.wants/*udev* ; \
    rm -rf /lib/systemd/system/sockets.target.wants/*initctl* ; \
    rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* ; \
    rm -rf /lib/systemd/system/systemd-update-utmp*

# Install requirements.
RUN apt-get update \
    && apt-get dist-upgrade -y \
    && apt-get install -y \
    python3 \
    sudo \
    gnupg \
    python3-apt \
    apt-transport-https \
    ca-certificates \
    && apt-get clean

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/lib/systemd/systemd"]
