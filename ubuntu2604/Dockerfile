# syntax=docker/dockerfile:1

FROM ubuntu:26.04

LABEL org.opencontainers.image.authors="Michael Buluma <me@buluma.co.ke>"
LABEL org.opencontainers.image.title="Docker Molecule Images - Ubuntu 26.04"
LABEL org.opencontainers.image.description="Ubuntu 26.04 (Provisional) for testing Ansible roles"
LABEL org.opencontainers.image.base.name="ubuntu:26.04"
LABEL org.opencontainers.image.licenses="Apache-2.0"
LABEL buluma.role-name="docker-molecule-images"

ENV container=docker
ENV DEBIAN_FRONTEND noninteractive

# Enable systemd.
RUN apt-get update && \
    apt-get install -y systemd python3 python3-pip sudo which shadow-utils && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    cd /lib/systemd/system/sysinit.target.wants/ && \
    ls | grep -v systemd-tmpfiles-setup | xargs rm -f && \
    rm -f /lib/systemd/system/multi-user.target.wants/* && \
    rm -f /etc/systemd/system/*.wants/* && \
    rm -f /lib/systemd/system/local-fs.target.wants/* && \
    rm -f /lib/systemd/system/sockets.target.wants/*udev* && \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl* && \
    rm -f /lib/systemd/system/basic.target.wants/* && \
    rm -f /lib/systemd/system/anaconda.target.wants/* && \
    rm -f /lib/systemd/system/plymouth* && \
    rm -f /lib/systemd/system/systemd-update-utmp* && \
    # Create docker user
    useradd -ms /bin/bash docker && \
    echo 'docker:docker' | chpasswd && \
    usermod -aG sudo docker && \
    # Allow docker user to run systemctl commands
    echo "docker ALL=(ALL) NOPASSWD: /usr/bin/systemctl" >> /etc/sudoers.d/docker && \
    # Clean up
    rm -rf /tmp/* /var/tmp/*

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]