FROM kalilinux/kali-rolling
LABEL maintainer="Michael Buluma"
LABEL build_date="2023-03-25"

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
