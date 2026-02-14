# SUSE Linux Enterprise Server 12

This directory is intended to house the Dockerfile for SUSE Linux Enterprise Server 12 (SLES 12).

## Important Note

SUSE Linux Enterprise Server is a commercial product and does not have freely available public container images. To build an SLES 12 container for Ansible testing, you would need:

1. A valid SUSE subscription
2. Access to the SUSE Customer Center to download the container image
3. Authentication to the registry.suse.com registry

## Building Instructions

If you have access to SLES container images, you can build this image using:

```bash
docker build -t sles12 .
```

## Alternative

Consider using openSUSE Leap or openSUSE Tumbleweed for testing if you don't have access to SLES subscriptions. These are available in the `opensuse` and `opensuse-tumbleweed` directories respectively.