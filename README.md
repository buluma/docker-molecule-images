# Docker Molecule Images

Docker Molecule Images for Testing Ansible Roles - A comprehensive collection of containerized Linux distributions designed specifically for testing Ansible playbooks across multiple operating systems.

## Overview

This project provides ready-to-use Docker images for numerous Linux distributions, enabling developers to test their Ansible roles in realistic environments without requiring full virtual machines. Each image is carefully configured with the appropriate init system (systemd, OpenRC, or upstart) to properly support service management during Ansible testing.

## Available Distributions

### Alpine Linux
- [alpine-openrc](alpine-openrc/) - Alpine Linux with OpenRC init system (Rolling release)

### Amazon Linux
- [amazonlinux2023](amazonlinux2023/) - Amazon Linux 2023 with systemd (EOL: June 2029)
- [amazonlinux2](amazonlinux2/) - Amazon Linux 2 with systemd ⚠️ *(Deprecated - EOL June 30, 2026)*
- [amazonlinux1](amazonlinux1/) - Amazon Linux 1 with upstart ⚠️ *(Deprecated - EOL July 2023)*

### Arch Linux
- [archlinux](archlinux/) - Arch Linux with systemd (Rolling release)

### CentOS
- [centos-stream9](centos-stream9/) - CentOS Stream 9 with systemd (Rolling)
- [centos7](centos7/) - CentOS 7 with systemd ⚠️ *(Deprecated - EOL June 2024)*

### Debian
- [debian13](debian13/) - Debian 13 (Trixie) with systemd (EOL: 2030)
- [debian12](debian12/) - Debian 12 (Bookworm) with systemd (EOL: 2028)
- [debian11](debian11/) - Debian 11 (Bullseye) with systemd (EOL: 2026)
- [debian10](debian10/) - Debian 10 (Buster) with systemd ⚠️ *(Deprecated - EOL June 2024)*
- [debian9](debian9/) - Debian 9 (Stretch) with systemd ⚠️ *(Deprecated - EOL June 2022)*

### Fedora
- [fedora45](fedora45/) - Fedora 45 with systemd (EOL: November 24, 2027)
- [fedora44](fedora44/) - Fedora 44 with systemd (EOL: June 2, 2027)
- [fedora43](fedora43/) - Fedora 43 with systemd (EOL: December 9, 2026)
- [fedora42](fedora42/) - Fedora 42 with systemd (EOL: May 27, 2026)
- [fedora41](fedora41/) - Fedora 41 with systemd ⚠️ *(Deprecated - EOL December 15, 2025)*
- [fedora40](fedora40/) - Fedora 40 with systemd ⚠️ *(Deprecated - EOL May 13, 2025)*
- [fedora39](fedora39/) - Fedora 39 with systemd ⚠️ *(Deprecated - EOL November 26, 2024)*
- [fedora38](fedora38/) - Fedora 38 with systemd ⚠️ *(Deprecated - EOL May 21, 2024)*
- [fedora37](fedora37/) - Fedora 37 with systemd ⚠️ *(Deprecated - EOL December 5, 2023)*

### Kali Linux
- [kalilinux](kalilinux/) - Kali Linux rolling with systemd (Rolling release)

### OpenSUSE
- [opensuse156](opensuse156/) - openSUSE Leap 15.6 with systemd (EOL: April 30, 2026)
- [opensuse-tumbleweed](opensuse-tumbleweed/) - openSUSE Tumbleweed with systemd (Rolling release)
- [opensuse](opensuse/) - OpenSUSE with systemd ⚠️ *(Deprecated - EOL Dec 2024)*

### Oracle Linux
- [oraclelinux9](oraclelinux9/) - Oracle Linux 9 with systemd (EOL: June 30, 2032; Extended: June 30, 2035)
- [oraclelinux8](oraclelinux8/) - Oracle Linux 8 with systemd (EOL: July 31, 2029; Extended: July 31, 2032)
- [oraclelinux7](oraclelinux7/) - Oracle Linux 7 with systemd ⚠️ *(Deprecated - EOL December 31, 2024; Extended: June 30, 2028)*

### Rocky Linux
- [rockylinux9](rockylinux9/) - Rocky Linux 9 with systemd (EOL: May 2032)
- [rockylinux8](rockylinux8/) - Rocky Linux 8 with systemd ⚠️ *(Deprecated - EOL May 2029)*
- [rockylinux10](rockylinux10/) - Rocky Linux 10 with systemd ⚠️ *(Deprecated - Base image not available)*

### AlmaLinux
- [almalinux10](almalinux10/) - AlmaLinux 10 with systemd (EOL: 2033)
- [almalinux9](almalinux9/) - AlmaLinux 9 with systemd (EOL: 2029)
- [almalinux8](almalinux8/) - AlmaLinux 8 with systemd (EOL: March 1, 2029)

### RHEL
- [rhel9](rhel9/) - Red Hat Enterprise Linux 9 with systemd (Full Support: May 2027; Maintenance: May 2032; ELC available)
- [rhel8-ubi](rhel8-ubi/) - Red Hat Enterprise Linux 8 (UBI) with systemd (Full Support: May 2029; Maintenance: May 2032; ELC available)

### SUSE
- [opensuse-tumbleweed](opensuse-tumbleweed/) - openSUSE Tumbleweed with systemd (Rolling release)
- [opensuse156](opensuse156/) - openSUSE Leap 15.6 with systemd (EOL: April 30, 2026)
- [sles15](sles15/) - SUSE Linux Enterprise Server 15 with systemd ⚠️ *(Deprecated - Auth required, systemd path issue)*
- [sles12](sles12/) - SUSE Linux Enterprise Server 12 with systemd ⚠️ *(Deprecated - Auth required)*

### Ubuntu
- [ubuntu2604](ubuntu2604/) - Ubuntu 26.04 LTS (Resolute Raccoon) with systemd (EOL: May 29, 2031; ESM: April 2036)
- [ubuntu2510](ubuntu2510/) - Ubuntu 25.10 (Questing Quokka) with systemd ⚠️ *(Deprecated - EOL July 9, 2026)*
- [ubuntu2504](ubuntu2504/) - Ubuntu 25.04 (Plucky Puffin) with systemd (EOL: January 15, 2026)
- [ubuntu2410](ubuntu2410/) - Ubuntu 24.10 (Oracular Oriole) with systemd ⚠️ *(Deprecated - EOL July 10, 2025)*
- [ubuntu2404](ubuntu2404/) - Ubuntu 24.04 LTS (Noble Numbat) with systemd (EOL: May 31, 2029; ESM: April 2034)
- [ubuntu2304](ubuntu2304/) - Ubuntu 23.04 (Lunar Lobster) with systemd ⚠️ *(Deprecated - EOL January 25, 2024)*
- [ubuntu2204](ubuntu2204/) - Ubuntu 22.04 LTS (Jammy Jellyfish) with systemd (EOL: June 1, 2027; ESM: April 2032)
- [ubuntu2004](ubuntu2004/) - Ubuntu 20.04 LTS (Focal Fossa) with systemd ⚠️ *(Deprecated - EOL May 29, 2025; ESM: April 2030)*
- [ubuntu1804](ubuntu1804/) - Ubuntu 18.04 LTS (Bionic Beaver) with systemd ⚠️ *(Deprecated - EOL April 2023; ESM: April 2028)*

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
[![amazonlinux-2023](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2023.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2023.yml)
[![amazonlinux-2](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/amazonlinux2.yml)


### Centos
[![centos-stream9](https://github.com/buluma/docker-molecule-images/actions/workflows/centos-stream9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/centos-stream9.yml)


### Debian
[![debian13](https://github.com/buluma/docker-molecule-images/actions/workflows/debian13.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian13.yml)
[![debian12](https://github.com/buluma/docker-molecule-images/actions/workflows/debian12.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian12.yml)
[![debian11](https://github.com/buluma/docker-molecule-images/actions/workflows/debian11.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/debian11.yml)



### Fedora
[![fedora45](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora45.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora45.yml)
[![fedora44](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora44.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora44.yml)
[![fedora43](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora43.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora43.yml)
[![fedora42](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora42.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora42.yml)
[![fedora41](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora41.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora41.yml)
[![fedora40](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora40.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/fedora40.yml)




### Kalilinux
[![kalilinux-rolling](https://github.com/buluma/docker-molecule-images/actions/workflows/kalilinux.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/kalilinux.yml)

### Opensuse
[![opensuse156](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse156.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse156.yml)

### Oraclelinux
[![oraclelinux-9](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux9.yml)
[![oraclelinux-8](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux8.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/oraclelinux8.yml)


### Rockylinux
[![rockylinux-9](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rockylinux9.yml)


### AlmaLinux
[![almalinux10](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux10.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux10.yml)
[![almalinux9](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux9.yml)
[![almalinux8](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux8.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/almalinux8.yml)

### RHEL
[![rhel9](https://github.com/buluma/docker-molecule-images/actions/workflows/rhel9.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rhel9.yml)
[![rhel8-ubi](https://github.com/buluma/docker-molecule-images/actions/workflows/rhel8-ubi.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/rhel8-ubi.yml)

### SUSE
[![opensuse-tumbleweed](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse-tumbleweed.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/opensuse-tumbleweed.yml)

### Ubuntu
[![ubuntu-26.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2604.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2604.yml)
[![ubuntu-25.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2504.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2504.yml)
[![ubuntu-24.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2404.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2404.yml)
[![ubuntu-22.04](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2204.yml/badge.svg)](https://github.com/buluma/docker-molecule-images/actions/workflows/ubuntu2204.yml)



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