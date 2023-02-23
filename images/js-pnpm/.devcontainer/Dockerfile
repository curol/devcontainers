FROM ghcr.io/curol/devcontainers/js:latest

ARG USERNAME=${USERNAME}
ARG PNPM_VERSION=${PNPM_VERSION}

RUN export DEBIAN_FRONTEND=noninteractive \
    # Install with corepack \
    && su -l $USERNAME /bin/zsh -c "source ~/.zshrc && corepack enable && corepack prepare pnpm@$PNPM_VERSION --activate" \
    # && su $USERNAME -s /usr/bin/zsh -c 'pnpm setup' \
    # Clean \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "JS/TS - PNPM development environment."