# syntax=docker/dockerfile:1

FROM clearlinux:latest

ARG CONTAINER_RUNTIME=docker

LABEL org.opencontainers.image.authors="Michael Buluma <me@buluma.co.ke>"
LABEL org.opencontainers.image.title="Docker Molecule Images - Clear Linux"
LABEL org.opencontainers.image.description="Clear Linux for testing Ansible roles"
LABEL org.opencontainers.image.base.name="clearlinux:latest"
LABEL org.opencontainers.image.licenses="Apache-2.0"
LABEL buluma.role-name="docker-molecule-images"

ENV container=${CONTAINER_RUNTIME}

# Clear Linux uses swupd for package management
# Install essential packages for Ansible testing
RUN swupd update && \
    swupd bundle-add \
        os-core \
        os-core-update \
        python3-basic \
        python3-cryptography \
        python3-pip \
        python3-setuptools \
        systemd \
        shadow-utils \
        sudo && \
    rm -rf /tmp/* /var/tmp/* /usr/share/doc/packages/*

# Install additional packages needed for Ansible testing
RUN python3 -m pip install --upgrade pip && \
    # Create docker user
    useradd -ms /bin/bash docker && \
    echo 'docker:docker' | chpasswd && \
    usermod -aG sys docker && \
    # Allow docker user to run systemctl commands
    echo "docker ALL=(ALL) NOPASSWD: /usr/bin/clr-service-restart" >> /etc/sudoers.d/docker && \
    # Clean up
    rm -rf /tmp/* /var/tmp/*

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/bin/init"]