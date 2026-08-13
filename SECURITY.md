# Security Policy

## Reporting a Vulnerability

Please do not disclose suspected vulnerabilities in a public issue.

Report security concerns privately to the repository owner through GitHub's private vulnerability reporting feature when available. If private reporting is unavailable, contact the maintainer privately before publishing technical details.

Include enough information to reproduce and assess the issue, but do not include real credentials, tokens, private keys, or other secrets.

## Secrets

This repository must not contain passwords, API keys, access tokens, private keys, session credentials, or production configuration containing secrets.

Use environment variables or an external secret store for sensitive values. Example configuration files must contain placeholders only.

## Scope

Security reports concerning the skill files, repository automation, release artifacts, or installation workflow are in scope.
