# Day 2 Docker Image Comparison

## Insecure Image

Image name: devsecops-app:insecure

Security concerns:

- Uses a larger base image
- Runs as root by default
- Uses pip cache
- Has larger attack surface
- More likely to contain unnecessary packages and vulnerabilities

## Hardened Image

Image name: devsecops-app:hardened

Security improvements:

- Uses python:3.11-slim
- Creates a dedicated non-root user
- Runs application as appuser
- Uses --no-cache-dir during dependency installation
- Reduces unnecessary image bloat
- Improves least privilege

## Key Lesson

Docker security starts with the Dockerfile. A container is not automatically secure just because it is isolated. The base image, user permissions, dependencies, and runtime configuration all affect risk.
