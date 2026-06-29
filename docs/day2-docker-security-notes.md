# Day 2: Docker Security Foundations

## Objective

The goal of Day 2 was to understand Docker security by building an insecure container image, scanning it, and then creating a hardened version.

## Tools Used

- Docker
- Flask
- Trivy
- Git
- GitHub
- Pre-commit
- GitLeaks

## Key Concepts

Docker packages applications and dependencies into containers. Images are templates, while containers are running instances of images. Docker uses Linux kernel features such as namespaces for isolation and cgroups for resource control.

## Insecure Dockerfile Findings

The insecure Dockerfile used a larger Python base image and did not create a non-root user. As a result, the container ran as root. This increases risk because if the application is compromised, the attacker has elevated privileges inside the container.

## Hardened Dockerfile Improvements

The hardened Dockerfile used a slim base image, installed dependencies without cache, created a dedicated non-root user, changed file ownership, and ran the application as that non-root user.

## Trivy Scanning

Trivy was used to scan both insecure and hardened images. The scan reports were saved under security/reports. The purpose of the scan was to identify vulnerabilities in base images and dependencies.

## Runtime Security

The insecure container ran as root. The hardened container ran as appuser. Running as a non-root user follows the principle of least privilege and reduces potential damage if the container is compromised.

## Dangerous Runtime Flags

The --privileged flag gives a container expanded access to host resources. This weakens container isolation and should be avoided in production.

## Security Lessons

Containers are not secure by default. Docker security depends on the Dockerfile, the base image, dependency management, user privileges, and runtime configuration. Smaller images and least privilege reduce risk.

## Secure Docker Workflow

1. Build image
2. Inspect image history
3. Run container
4. Verify runtime user
5. Scan with Trivy
6. Harden Dockerfile
7. Rescan
8. Compare results
9. Commit reports and documentation

## Key Takeaway

Docker security begins before deployment. A secure container should be built from a trusted base image, run as a non-root user, minimize unnecessary packages, and be scanned before release.
