# syntax=docker/dockerfile:1

FROM sles12sp5:latest

ARG CONTAINER_RUNTIME=docker

LABEL org.opencontainers.image.authors="Michael Buluma <me@buluma.co.ke>"
LABEL org.opencontainers.image.title="Docker Molecule Images - SLES 12"
LABEL org.opencontainers.image.description="SUSE Linux Enterprise Server 12 for testing Ansible roles"
LABEL org.opencontainers.image.base.name="sles12sp5:latest"
LABEL org.opencontainers.image.licenses="Apache-2.0"
LABEL buluma.role-name="docker-molecule-images"

ENV container=${CONTAINER_RUNTIME}
ENV init=/usr/lib/systemd/systemd

RUN zypper refresh && \
    zypper install -y \
        python3 \
        python3-pip \
        systemd \
        which \
        shadow \
        sudo && \
    zypper clean -a && \
    rm -rf /tmp/* /var/tmp/* /usr/share/doc/packages/*

# Install additional packages needed for Ansible testing
RUN python3 -m pip install --upgrade pip && \
    touch /usr/sbin/policy-rc.d && \
    chmod 755 /usr/sbin/policy-rc.d && \
    systemctl mask \
        dev-hugepages.mount \
        sys-fs-fuse-connections.mount \
        systemd-logind.service \
        systemd-networkd.service \
        systemd-resolved.service

# Allow docker user to run systemctl commands
RUN echo "docker ALL=(ALL) NOPASSWD: /usr/bin/systemctl" >> /etc/sudoers.d/docker

# Create docker user
RUN useradd -ms /bin/bash docker && \
    echo 'docker:docker' | chpasswd && \
    usermod -aG wheel docker

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/sbin/init"]