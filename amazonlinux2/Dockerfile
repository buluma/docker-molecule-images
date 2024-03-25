FROM amazonlinux:2
LABEL maintainer="buluma"
LABEL build_date="2024-03-24"
ENV container=docker

ENV pip_packages "ansible"

# Install systemd -- See https://hub.docker.com/_/centos/
RUN yum -y update; yum clean all

# Install requirements. # TODO https://github.com/robertdebock/docker-amazonlinux-systemd/blob/master/Dockerfile
RUN yum makecache fast \
 && yum -y install deltarpm epel-release initscripts systemd \
 && yum -y update \
 && yum -y install \
      sudo \
      which \
      python-pip \
 && yum clean all

# Install Ansible via Pip.
RUN pip install $pip_packages

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

# Install Ansible inventory file.
RUN mkdir -p /etc/ansible
RUN echo -e '[local]\nlocalhost ansible_connection=local' > /etc/ansible/hosts

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
