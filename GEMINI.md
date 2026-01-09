# Docker Molecule Images

## Project Overview

This repository contains a collection of Docker images specifically optimized for testing Ansible roles using [Molecule](https://molecule.readthedocs.io/).
The primary goal is to provide lightweight, pre-configured containers that mimic real operating systems, complete with working init systems (systemd, OpenRC, upstart). This allows for realistic service testing (e.g., `systemctl start my-service`) within a containerized environment.

**Key Features:**
*   **Init Systems:** Properly configured `systemd` (most distros), `OpenRC` (Alpine), or `upstart` (Amazon Linux 1).
*   **Multi-Architecture:** Images are often built for multiple architectures (amd64, arm64, etc.).
*   **Variety:** Supports Alpine, Amazon Linux, Arch, CentOS, Debian, Fedora, Kali, OpenSUSE, Oracle Linux, Rocky Linux, and Ubuntu.

## Architecture

*   **Directory Structure:** Each distribution version has its own dedicated directory (e.g., `ubuntu2404/`, `rockylinux9/`).
*   **Dockerfiles:** Located within the distro directory. They typically start from a base image (e.g., `ubuntu:noble`), install the init system, clean up unnecessary services, and set up the environment.
*   **Dependencies:** Some images (like `rockylinux9`) include a `requirements.txt` and install Ansible/Molecule dependencies via pip. Others (like `ubuntu2404`) are more minimal.

## Building and Running

### Building an Image

Navigate to the specific distribution directory and run standard Docker commands.

```bash
cd ubuntu2404
docker build -t local/ubuntu2404 .
```

### Using Makefiles

Some directories (e.g., `ubuntu2404`) contain a `Makefile` to simplify building, especially for multi-architecture support.

```bash
cd ubuntu2404
make docker-build       # Build local image
# make docker-build-multi-arch  # Build for multiple architectures (requires buildx)
```

### Running the Container

**Crucial:** To allow systemd (or other init systems) to function correctly, you must run the container with elevated privileges and mount the cgroup volume.

```bash
docker run -it --rm \
  --privileged \
  -v /sys/fs/cgroup:/sys/fs/cgroup:rw \
  local/ubuntu2404
```

### Usage with Molecule

In your `molecule.yml`:

```yaml
driver:
  name: docker
platforms:
  - name: instance
    image: ghcr.io/buluma/ubuntu2404:latest
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    cgroupns_mode: host
```

## Development Conventions

*   **Naming:** Directories are named in the format `<distro><version>` (no separators), e.g., `debian12`, `fedora40`.
*   **Dockerfile:**
    *   Use `# syntax=docker/dockerfile:1`.
    *   Include OpenContainers labels (`maintainer`, `build_date`, `title`, `description`, etc.).
    *   Set `ENV container docker`.
    *   Perform cleanup of systemd unit files to prevent conflicts in a containerized environment.
*   **CI/CD:**
    *   Workflows are defined in `.github/workflows/`.
    *   Typically, there is one workflow file per distribution family or specific version (e.g., `multi-noble.yml`, `debian12.yml`).
    *   Workflows handle building, testing, and pushing to Docker Hub/GHCR.
*   **Contribution:**
    *   To add a new distro: Create a new directory, add `Dockerfile`, and create a corresponding workflow in `.github/workflows/`.
