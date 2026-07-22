# syntax=docker/dockerfile:1
FROM debian:trixie

LABEL maintainer="buluma"
LABEL build_date="2025-12-01"

LABEL org.opencontainers.image.title="Docker Debian Trixie Systemd" \
      org.opencontainers.image.description="Ubuntu Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker
ENV DEBIAN_FRONTEND noninteractive

# Enable systemd.
RUN apt-get update ; \
    apt-get install -y sudo systemd systemd-sysv; \
    apt-get clean ; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* ; \
    rm -rf /lib/systemd/system/multi-user.target.wants/* ; \
    rm -rf /etc/systemd/system/*.wants/* ; \
    rm -rf /lib/systemd/system/local-fs.target.wants/* ; \
    rm -rf /lib/systemd/system/sockets.target.wants/*udev* ; \
    rm -rf /lib/systemd/system/sockets.target.wants/*initctl* ; \
    rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* ; \
    rm -rf /lib/systemd/system/systemd-update-utmp* ; \
    # Trixie's systemd no longer creates /run/lock as a built-in startup
    # fallback (older systemd, e.g. bookworm's, did); without this unit
    # enabled, /run/lock (and the /var/lock symlink to it) never gets
    # created, breaking any service whose init script locks there
    # (e.g. apache2ctl's mktemp under /var/lock).
    mkdir -p /lib/systemd/system/sysinit.target.wants ; \
    ln -sf /lib/systemd/system/systemd-tmpfiles-setup.service /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup.service ; \
    # Fix PAM for container environments — allow sudo without password
    (mkdir -p /etc/pam.d/sudo.d && echo 'auth sufficient pam_permit.so' > /etc/pam.d/sudo.d/docker-container || \
     sed -i '1iauth sufficient pam_permit.so' /etc/pam.d/sudo) ; \
    # Pre-configure passwordless sudo for sudo group (Debian convention)
    echo '%sudo ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/molecule ; \
    chmod 0440 /etc/sudoers.d/molecule

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/lib/systemd/systemd"]
