# syntax=docker/dockerfile:1
FROM debian:buster

LABEL maintainer="buluma"
LABEL build_date="2024-03-27"
LABEL org.opencontainers.image.title="Docker Ubuntu Noble Systemd"
LABEL org.opencontainers.image.description="Ubuntu Container for Ansible Tests."
LABEL org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/"
LABEL org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images"
LABEL org.opencontainers.image.licenses="Apache-2.0"

ARG DEBIAN_FRONTEND=noninteractive

# Enable apt repositories.
RUN sed -i 's/# deb/deb/g' /etc/apt/sources.list

# Install dependencies.
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential wget libffi-dev libssl-dev procps gnupg \
    python3-pip python3-dev python3-setuptools python3-wheel python3-apt python3-cryptography \
    sudo systemd systemd-sysv \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /usr/share/doc /usr/share/man /tmp/* /var/tmp/* \
    && rm -rf /lib/systemd/system/multi-user.target.wants/* \
    && rm -rf /etc/systemd/system/*.wants/* \
    && rm -rf /lib/systemd/system/local-fs.target.wants/* \
    && rm -rf /lib/systemd/system/sockets.target.wants/*udev* \
    && rm -rf /lib/systemd/system/sockets.target.wants/*initctl* \
    && rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* \
    && rm -rf /lib/systemd/system/systemd-update-utmp*

# Install cryptography and Ansible via pip.
RUN pip3 install --no-cache-dir cryptography ansible

# Upgrade pip to latest version.
RUN pip3 install --no-cache-dir --upgrade pip

COPY initctl_faker /sbin/initctl
RUN chmod +x /sbin/initctl

# Install Ansible inventory file.
RUN echo "[local]\nlocalhost ansible_connection=local" > /etc/ansible/hosts

# Make sure systemd doesn't start agettys on tty[1-6].
RUN rm -f /lib/systemd/system/multi-user.target.wants/getty.target

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
