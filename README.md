# devcontainer-docker

Example Devcontainer for use with GitHub CodeSpaces that includes Docker

via a Dockerfile manual install

----

You should probably not actually use this method. You should probably do something like this instead, which includes Docker via Devcontainer "features" https://containers.dev/features

```
{
    "image": "mcr.microsoft.com/devcontainers/base:1.2.4-ubuntu24.04",
    "features": {
        "ghcr.io/devcontainers/features/sshd:1": {
            "version": "latest"
        },
        "ghcr.io/devcontainers/features/docker-in-docker:2": {},
        "ghcr.io/devcontainers-extra/features/ansible:2": {},
        "ghcr.io/rocker-org/devcontainer-features/miniforge:2": {
            "version": "25.1.1-2"
        },
        "ghcr.io/devcontainers/features/github-cli:1": {},
        "ghcr.io/eitsupi/devcontainer-features/jq-likes:2": {},
        "ghcr.io/robsyme/features/nextflow:1": {},
        "ghcr.io/robsyme/features/nf-test:1": {},
        "ghcr.io/devcontainer-community/devcontainer-features/btop:1": {},
        "ghcr.io/devcontainers/features/aws-cli:1": {},
        "ghcr.io/devcontainers-extra/features/tmux-apt-get:1": {},
        "ghcr.io/devcontainers-extra/features/wget-apt-get:1": {},
        "ghcr.io/devcontainers-extra/features/micro:1": {},
        "ghcr.io/devcontainers-extra/features/apt-get-packages:1": {
            "packages": "screen,singularity-container=4.1.1+ds2-1ubuntu0.2"
        }
    },
    "hostRequirements": {
        "cpus": 4,
        "memory": "16gb",
        "storage": "64gb"
    }
}

```
