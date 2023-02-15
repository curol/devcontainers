FROM ghcr.io/curol/devcontainers/debian:latest

ARG NODE_VERSION=${NODE_VERSION}
ARG TERM=xterm-256color

RUN export DEBIAN_FRONTEND=noninteractive \
    # Install node \
    && curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION}.x | sudo bash - \
    && apt-get update \
    && apt-get -y upgrade \
    && apt-get install -y nodejs \
    # Clean \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "JS/TS development environment."