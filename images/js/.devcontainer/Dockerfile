FROM ghcr.io/curol/devcontainers/debian:latest

ARG NODE_VERSION=${NODE_VERSION}
ARG TERM=xterm-256color
ARG NVM_VER=${NVM_VER:-"0.39.3"}

RUN export DEBIAN_FRONTEND=noninteractive \
    # Install nvm \
    && su -l vscode /bin/zsh -c "curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v${NVM_VER}/install.sh | bash" \
    && su -l vscode /bin/zsh -c 'source ~/.zshrc && nvm install --lts' \
    # Clean \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "Node & JS development environment."