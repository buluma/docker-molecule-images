# Docker Molecule Images - Project Context

## Project Overview
This is a comprehensive collection of Docker images specifically designed for testing Ansible roles using Molecule. The project provides a wide range of Linux distributions in containerized formats, allowing developers to test their Ansible playbooks across multiple operating systems without requiring full VMs.

The project contains Dockerfiles for numerous Linux distributions including:
- Alpine Linux (with OpenRC)
- Amazon Linux (versions 1, 2, and 2023)
- Arch Linux
- CentOS (version 7)
- Debian (versions 9, 10, 11, 12, and 13)
- Fedora (versions 37-41)
- Kali Linux
- OpenSUSE
- Oracle Linux (versions 7, 8, 9)
- Rocky Linux (versions 8, 9, 10)
- Ubuntu (versions 18.04, 20.04, 22.04, 23.04, 24.04, 25.04)

Each distribution directory contains a Dockerfile that creates a containerized environment suitable for Ansible role testing, with appropriate init systems (systemd, OpenRC, or upstart) configured to run properly in containerized environments.

## Architecture and Implementation
The project follows a consistent pattern across all distributions:
- Each distribution has its own directory with a Dockerfile
- Dockerfiles are configured with proper init systems to support services during Ansible testing
- Labels follow the OpenContainers specification for standardized metadata
- Common environment variables are set (container=docker, DEBIAN_FRONTEND=noninteractive)
- Volumes are configured for cgroup access to support systemd/OpenRC in containers

Different distributions use appropriate init systems:
- Debian/Ubuntu/Rocky/Oracle: systemd-based
- Alpine: OpenRC-based
- Amazon Linux 1: upstart-based

## Building and Running

### Building Individual Images
To build a specific distribution image:
```bash
cd <distribution-directory>
docker build -t <distribution-name> .
```

For example:
```bash
cd ubuntu2204
docker build -t ubuntu2204 .
```

### Using the Images with Molecule
These images are designed to be used with Ansible Molecule for testing roles. In your molecule.yml configuration:

```yaml
driver:
  name: docker
platforms:
  - name: instance
    image: buluma/<distribution>:tag
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    cgroupns_mode: host
```

### Automated Builds
The project uses GitHub Actions for automated builds and testing. Each distribution has its own workflow file in `.github/workflows/` that:
1. Tests the image builds correctly
2. Runs the built image to verify functionality
3. Pushes the image to Docker Hub and GitHub Container Registry when changes are merged to the master branch
4. Builds for multiple architectures (amd64, arm64, arm/v6, arm/v7, arm64/v8, ppc64le, s390x, 386)

## Development Conventions
- All Dockerfiles use the modern Dockerfile syntax: `# syntax=docker/dockerfile:1`
- Standardized labels following OpenContainers specifications
- Consistent volume mounting for cgroup access
- Proper init system configuration for containerized environments
- Pre-commit hooks are configured for code quality (check-case-conflict, check-merge-conflict, check-symlinks, check-json, check-yaml, detect-private-key, end-of-file-fixer, trailing-whitespace, double-quote-string-fixer)
- Renovate bot is configured for dependency updates

## Key Files and Directories
- `README.md`: Contains build status badges for all supported distributions
- `.pre-commit-config.yaml`: Configuration for pre-commit hooks
- `.github/workflows/`: Individual workflow files for each distribution
- `LICENSE`: Apache 2.0 license
- `renovate.json`: Configuration for automated dependency updates

## Purpose and Usage
This project serves the Ansible community by providing reliable, consistently-built container images for testing Ansible roles across multiple Linux distributions. It eliminates the need for developers to create their own test containers and ensures consistent testing environments.

The images are published to Docker Hub under the `buluma` namespace and GitHub Container Registry, making them readily available for use in Molecule-based testing workflows.