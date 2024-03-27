# syntax=docker/dockerfile:1
FROM alpine:3

LABEL maintainer="Michael Buluma <me@buluma.me.ke>"
LABEL build_date="2024-03-27"

LABEL org.opencontainers.image.title="Docker Ubuntu Noble Systemd" \
      org.opencontainers.image.description="Ubuntu Container for Ansible Tests." \
      org.opencontainers.image.url="https://github.com/buluma/docker-molecule-images/" \
      org.opencontainers.image.source="https://github.com/buluma/docker-molecule-images" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV container=docker

# Enable init.
RUN apk add --update --no-cache openrc && \
    sed -i 's/^\(tty\d\:\:\)/#\1/g' /etc/inittab && \
    sed -i \
      -e 's/#rc_sys=".*"/rc_sys="docker"/g' \
      -e 's/#rc_env_allow=".*"/rc_env_allow="\*"/g' \
      -e 's/#rc_crashed_stop=.*/rc_crashed_stop=NO/g' \
      -e 's/#rc_crashed_start=.*/rc_crashed_start=YES/g' \
      -e 's/#rc_provide=".*"/rc_provide="loopback net"/g' \
      /etc/rc.conf && \
    rm -f /etc/init.d/hwdrivers \
      /etc/init.d/hwclock \
      /etc/init.d/hwdrivers \
      /etc/init.d/modules \
      /etc/init.d/modules-load \
      /etc/init.d/modloop && \
    sed -i 's/cgroup_add_service /# cgroup_add_service /g' /lib/rc/sh/openrc-run.sh && \
    sed -i 's/VSERVER/DOCKER/Ig' /lib/rc/sh/init.sh

VOLUME ["/sys/fs/cgroup"]

CMD ["/sbin/init"]
