FROM mcr.microsoft.com/devcontainers/base:ubuntu

RUN apt-get update \
    && apt-get install -y \
        pre-commit \
    && rm -rf /var/lib/apt/lists/*
