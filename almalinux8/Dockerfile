# syntax=docker/dockerfile:1
FROM almalinux:8

LABEL maintainer="Michael Buluma <me@buluma.me.ke>"
LABEL build_date="2026-07-11"

LABEL org.opencontainers.image.title="AlmaLinux 8 Systemd" \
      org.opencontainers.image.description="AlmaLinux 8 Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker
ENV DEBIAN_FRONTEND=noninteractive

# Enable systemd.
RUN if command -v microdnf >/dev/null 2>&1; then \
      microdnf install -y systemd systemd-sysv sudo && microdnf clean all; \
    elif command -v dnf >/dev/null 2>&1; then \
      dnf install -y systemd systemd-sysv sudo && dnf clean all; \
    else \
      yum install -y systemd systemd-sysv sudo && yum clean all; \
    fi && \
    rm -rf /var/cache/dnf && \
    rm -rf /lib/systemd/system/multi-user.target.wants/* && \
    rm -rf /etc/systemd/system/*.wants/* && \
    rm -rf /lib/systemd/system/local-fs.target.wants/* && \
    rm -rf /lib/systemd/system/sockets.target.wants/*udev* && \
    rm -rf /lib/systemd/system/sockets.target.wants/*initctl* && \
    rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* && \
    rm -rf /lib/systemd/system/systemd-update-utmp* && \
    # Fix PAM for container environments — allow sudo without password
    (mkdir -p /etc/pam.d/sudo.d && echo 'auth sufficient pam_permit.so' > /etc/pam.d/sudo.d/docker-container || \
     sed -i '1iauth sufficient pam_permit.so' /etc/pam.d/sudo) && \
    # Pre-configure passwordless sudo for wheel group
    groupadd -f wheel && \
    echo '%wheel ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/molecule && \
    chmod 0440 /etc/sudoers.d/molecule

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/lib/systemd/systemd"]
