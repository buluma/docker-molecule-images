FROM rockylinux:8
LABEL maintainer="Michael Buluma"
LABEL build_date="2024-03-25"

ENV container=docker

ENV pip_packages "ansible"

# Install systemd -- See https://hub.docker.com/_/centos/
RUN yum -y install rpm dnf-plugins-core \
 && yum -y update \
 && yum -y install \
      epel-release \
      initscripts \
      which \
      hostname \
      libyaml \
      python3 \
      python3-pip \
      python3-pyyaml \
      sudo \
 && yum clean all && \
    # Fix PAM for container environments — allow sudo without password.
    # /etc/pam.d/sudo has no sudo.d include on EL, so patch it directly for
    # both the auth and account phases (sudo's account check fails otherwise).
    sed -i '1iaccount sufficient pam_permit.so' /etc/pam.d/sudo && \
    sed -i '1iauth sufficient pam_permit.so' /etc/pam.d/sudo && \
    # Pre-configure passwordless sudo for wheel group
    groupadd -f wheel && \
    echo '%wheel ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/molecule && \
    chmod 0440 /etc/sudoers.d/molecule

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
