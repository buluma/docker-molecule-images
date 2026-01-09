# Docker Molecule Images

Docker Molecule Images for Testing Ansible Roles - A comprehensive collection of containerized Linux distributions designed specifically for testing Ansible playbooks across multiple operating systems.

## Overview

This project provides ready-to-use Docker images for numerous Linux distributions, enabling developers to test their Ansible roles in realistic environments without requiring full virtual machines. Each image is carefully configured with the appropriate init system (systemd, OpenRC, or upstart) to properly support service management during Ansible testing.

## Available Distributions

### Alpine Linux
- [alpine-openrc](alpine-openrc/) - Alpine Linux with OpenRC init system

### Amazon Linux
- [amazonlinux1](amazonlinux1/) - Amazon Linux 1 with upstart ⚠️ *(Deprecated - EOL July 2023)*
- [amazonlinux2](amazonlinux2/) - Amazon Linux 2 with systemd
- [amazonlinux2023](amazonlinux2023/) - Amazon Linux 2023 with systemd

### Arch Linux
- [archlinux](archlinux/) - Arch Linux with systemd

### CentOS
- [centos7](centos7/) - CentOS 7 with systemd ⚠️ *(Deprecated - EOL June 2024)*
- [centos-stream9](centos-stream9/) - CentOS Stream 9 with systemd

### Debian
- [debian9](debian9/) - Debian 9 (Stretch) with systemd ⚠️ *(Deprecated - EOL June 2022)*
- [debian10](debian10/) - Debian 10 (Buster) with systemd ⚠️ *(Deprecated - EOL June 2024)*
- [debian11](debian11/) - Debian 11 (Bullseye) with systemd
- [debian12](debian12/) - Debian 12 (Bookworm) with systemd
- [debian13](debian13/) - Debian 13 (Trixie) with systemd

### Fedora
- [fedora37](fedora37/) - Fedora 37 with systemd ⚠️ *(Deprecated - EOL November 2023)*
- [fedora38](fedora38/) - Fedora 38 with systemd ⚠️ *(Deprecated - EOL May 2024)*
- [fedora39](fedora39/) - Fedora 39 with systemd ⚠️ *(Deprecated - EOL November 2024)*
- [fedora40](fedora40/) - Fedora 40 with systemd
- [fedora41](fedora41/) - Fedora 41 with systemd
- [fedora42](fedora42/) - Fedora 42 with systemd
- [fedora43](fedora43/) - Fedora 43 with systemd

### Kali Linux
- [kalilinux](kalilinux/) - Kali Linux rolling with systemd

### OpenSUSE
- [opensuse](opensuse/) - OpenSUSE with systemd

### Oracle Linux
- [oraclelinux7](oraclelinux7/) - Oracle Linux 7 with systemd ⚠️ *(Deprecated - EOL June 2024)*
- [oraclelinux8](oraclelinux8/) - Oracle Linux 8 with systemd
- [oraclelinux9](oraclelinux9/) - Oracle Linux 9 with systemd

### Rocky Linux
- [rockylinux8](rockylinux8/) - Rocky Linux 8 with systemd ⚠️ *(Deprecated - EOL May 2025)*
- [rockylinux9](rockylinux9/) - Rocky Linux 9 with systemd
- [rockylinux10](rockylinux10/) - Rocky Linux 10 with systemd

### AlmaLinux
- [almalinux9](almalinux9/) - AlmaLinux 9 with systemd
- [almalinux10](almalinux10/) - AlmaLinux 10 with systemd

### RHEL
- [rhel9](rhel9/) - Red Hat Enterprise Linux 9 with systemd

### SUSE
- [sles15](sles15/) - SUSE Linux Enterprise Server 15 with systemd
- [opensuse-tumbleweed](opensuse-tumbleweed/) - openSUSE Tumbleweed with systemd

### Ubuntu
- [ubuntu1804](ubuntu1804/) - Ubuntu 18.04 (Bionic) with systemd ⚠️ *(Deprecated - EOL April 2023)*
- [ubuntu2004](ubuntu2004/) - Ubuntu 20.04 (Focal) with systemd ⚠️ *(Deprecated - EOL April 2025)*
- [ubuntu2204](ubuntu2204/) - Ubuntu 22.04 (Jammy) with systemd
- [ubuntu2304](ubuntu2304/) - Ubuntu 23.04 (Lunar) with systemd
- [ubuntu2404](ubuntu2404/) - Ubuntu 24.04 (Noble) with systemd
- [ubuntu2410](ubuntu2410/) - Ubuntu 24.10 (Oracular) with systemd
- [ubuntu2504](ubuntu2504/) - Ubuntu 25.04 (Plucky) with systemd
- [ubuntu2510](ubuntu2510/) - Ubuntu 25.10 with systemd

## Usage

### With Ansible Molecule

Add to your `molecule.yml` configuration:

```yaml
driver:
  name: docker

platforms:
  - name: instance
    image: ghcr.io/buluma/<distribution>:latest
    # Or use Docker Hub: docker.io/buluma/<distribution>:latest
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    cgroupns_mode: host
    command: ""
    tty: true
```

### Standalone Usage

Pull and run any image directly:

```bash
# Pull the image
docker pull ghcr.io/buluma/ubuntu2204:latest

# Run interactively
docker run -it --rm --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:rw ghcr.io/buluma/ubuntu2204:latest
```

## Build Status

### Alpine
[![alpine-openrc](https://github.com/buluma/docker-molecule-images/actions/workflows/alpine-openrc.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/alpine-openrc.yml)

### Archlinux
[![archlinux](https://github.com/buluma/docker-molecule-images/actions/workflows/archlinux.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/archlinux.yml)

### Amazonlinux
[![amazonlinux-1](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux1.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux1.yml)
[![amazonlinux-2](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2.yml)
[![amazonlinux-2023](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2023.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2023.yml)

### Centos
[![centos-7](https://github.com/buluma/docker-molecule-images/actions/workflows/centos7.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/centos7.yml)
[![centos-stream9](https://github.com/buluma/docker-molecule-images/actions/workflows/centos-stream9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/centos-stream9.yml)

### Debian
[![debian9](https://github.com/buluma/docker-molecule-images/actions/workflows/debian9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian9.yml)
[![debian10](https://github.com/buluma/docker-molecule-images/actions/workflows/debian10.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian10.yml)
[![debian11](https://github.com/buluma/docker-molecule-images/actions/workflows/debian11.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian11.yml)
[![debian12](https://github.com/buluma/docker-molecule-images/actions/workflows/debian12.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian12.yml)
[![debian13](https://github.com/buluma/docker-molecule-images/actions/workflows/debian13.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian13.yml)

### Fedora
[![fedora37](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora37.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora37.yml)
[![fedora38](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora38.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora38.yml)
[![fedora39](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora39.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora39.yml)
[![fedora40](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora40.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora40.yml)
[![fedora41](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora41.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora41.yml)
[![fedora42](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora42.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora42.yml)
[![fedora43](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora43.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora43.yml)

### Kalilinux
[![kalilinux-rolling](https://github.com/buluma/docker-molecule-images/actions/workflows/kalilinux.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/kalilinux.yml)

### Opensuse
[![opensuse](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse.yml)

### Oraclelinux
[![oraclelinux-7](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux7.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux7.yml)
[![oraclelinux-8](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux8.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux8.yml)
[![oraclelinux-9](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux9.yml)

### Rockylinux
[![rockylinux-8](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux8.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux8.yml)
[![rockylinux-9](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux9.yml)
[![rockylinux-10](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux10.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux10.yml)

### AlmaLinux
[![almalinux9](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux9.yml)
[![almalinux10](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux10.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux10.yml)

### RHEL
[![rhel9](https://github.com/buluma/docker-molecule-images/actions/workflows/rhel9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rhel9.yml)

### SUSE
[![sles15](https://github.com/buluma/docker-molecule-images/actions/workflows/sles15.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/sles15.yml)
[![opensuse-tumbleweed](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse-tumbleweed.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse-tumbleweed.yml)

### Ubuntu
[![ubuntu-18.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu1804.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu1804.yml)
[![ubuntu-20.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2004.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2004.yml)
[![ubuntu-22.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2204.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2204.yml)
[![ubuntu-23.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2304.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2304.yml)
[![ubuntu-24.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2404.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2404.yml)
[![ubuntu-24.10](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2410.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2410.yml)
[![ubuntu-25.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2504.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2504.yml)
[![ubuntu-25.10](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2510.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2510.yml)

## Features

- ✅ **Multi-Architecture Support**: Images built for multiple architectures (amd64, arm64, arm/v6, arm/v7, ppc64le, s390x, 386)
- ✅ **Proper Init Systems**: Each distribution configured with appropriate init system for service testing
- ✅ **Security Scanning**: Integrated with Docker Scout for automated vulnerability assessments
- ✅ **Mandatory Verification**: All releases are verified via CI tests before deployment
- ✅ **Consistent Interface**: Uniform configuration approach across all distributions
- ✅ **Regular Updates**: Automated builds with Renovate bot for keeping base images current
- ✅ **CI/CD Ready**: Optimized for use in continuous integration pipelines

## Contributing

1. Fork the repository
2. Create a new branch for your distribution
3. Add a new directory with your Dockerfile
4. Create a corresponding workflow in `.github/workflows/`
5. Submit a pull request

## License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for more information.

## Author Information

Created and maintained by Michael Buluma ([@buluma](https://github.com/buluma))
