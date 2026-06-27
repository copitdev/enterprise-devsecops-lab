# Day 1 Summary: Secure GitOps Foundations

## What I Built

I created a secure DevSecOps repository with structured folders, GitHub SSH authentication, branch strategy, secret scanning, pre-commit hooks, repository security policies, and code ownership.

## Tools Used

- Git
- GitHub
- SSH
- GPG
- GitLeaks
- Pre-commit

## Security Controls Implemented

- SSH authentication
- GitLeaks secret scanning
- Custom secret detection rule
- Pre-commit hook enforcement
- Branch protection
- CODEOWNERS
- SECURITY.md
- Signed commits

## Key Lessons

Git is not just code storage. It is a security boundary and the root of trust for the DevSecOps pipeline. Secrets should never be committed, and if exposed, they must be considered compromised. Branch protection prevents unsafe changes from reaching production branches. Signed commits improve trust by proving commit authorship.

## Attack Simulation

I tested secret detection and unsafe branch behavior. GitLeaks successfully detected custom fake secrets using a custom rule. Branch protection is used to prevent direct unsafe pushes to protected branches.

## Secure Workflow

git status
git branch
gitleaks dir . --config .gitleaks.toml
pre-commit run --all-files
git add .
git commit -S -m "message"
git push
