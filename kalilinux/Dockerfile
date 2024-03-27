# syntax=docker/dockerfile:1
FROM kalilinux/kali-rolling
LABEL maintainer="Michael Buluma"
LABEL build_date="2024-03-27"

LABEL org.opencontainers.image.title="Docker Ubuntu Noble Systemd" \
      org.opencontainers.image.description="Ubuntu Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

RUN apt-get update \
  && apt-get install -y --no-install-recommends --allow-downgrades \
    apt-utils \
    bash \
    iproute2 \
    locales \
    python3 \
    sudo \
    systemd \
    systemd-cron  \
  && apt-get clean \
  && rm -Rf /var/lib/apt/lists/*

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
CMD ["/lib/systemd/systemd"]
