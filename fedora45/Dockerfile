# syntax=docker/dockerfile:1

FROM fedora:45

LABEL org.opencontainers.image.authors="Michael Buluma <me@buluma.co.ke>"
LABEL org.opencontainers.image.title="Docker Molecule Images - Fedora 45"
LABEL org.opencontainers.image.description="Fedora 45 for testing Ansible roles"
LABEL org.opencontainers.image.base.name="fedora:45"
LABEL org.opencontainers.image.licenses="Apache-2.0"
LABEL buluma.role-name="docker-molecule-images"

ENV container=docker

# Enable systemd.
RUN dnf -y install systemd python3-libdnf5 python3-libdnf5-cli && dnf clean all && \
  (cd /lib/systemd/system/sysinit.target.wants/ ; for i in * ; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i ; done) ; \
  rm -f /lib/systemd/system/multi-user.target.wants/* ;\
  rm -f /etc/systemd/system/*.wants/* ;\
  rm -f /lib/systemd/system/local-fs.target.wants/* ; \
  rm -f /lib/systemd/system/sockets.target.wants/*udev* ; \
  rm -f /lib/systemd/system/sockets.target.wants/*initctl* ; \
  rm -f /lib/systemd/system/basic.target.wants/* ; \
  rm -f /lib/systemd/system/anaconda.target.wants/* && \
  # Install additional packages needed for Ansible testing
  dnf -y install python3 python3-pip sudo which shadow-utils && \
  # Create docker user
  useradd -ms /bin/bash docker && \
  echo 'docker:docker' | chpasswd && \
  usermod -aG wheel docker && \
  # Allow docker user to run systemctl commands
  echo "docker ALL=(ALL) NOPASSWD: /usr/bin/systemctl" >> /etc/sudoers.d/docker && \
  # Clean up
  dnf clean all

VOLUME ["/sys/fs/cgroup"]
CMD ["/sbin/init"]
