FROM ghcr.io/curol/devcontainers/js:latest

ARG USERNAME=${USERNAME}
ARG PNPM_VERSION=${PNPM_VERSION}
ARG PNPM_GLOBAL_PACKAGES=${PNPM_GLOBAL_PACKAGES}

RUN export DEBIAN_FRONTEND=noninteractive \
    # Install with corepack \
    && corepack enable \
    && su $USERNAME -c "corepack prepare pnpm@$PNPM_VERSION --activate" \
    && su $USERNAME -s /usr/bin/zsh -c 'pnpm setup' \
    # Clean \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "JS/TS - PNPM development environment."