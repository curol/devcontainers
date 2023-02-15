#################################################
# BASE IMAGE 
# [Choice] Debian version (use bullseye on local arm64/Apple Silicon): bullseye, buster
#################################################
ARG VARIANT="bullseye"
FROM buildpack-deps:${VARIANT}-curl

#################################################
# RUN
# Install common tools and user environment.
#################################################
ARG PACKAGES="fzf ripgrep fd-find tree git ca-certificates curl wget netbase bat"

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    # Install packages \
    && apt-get -y install --no-install-recommends ${PACKAGES} \
    # Link fdfind \
    && ln -s $(which fdfind) /usr/bin/fd \
    # Install neovim \
    && mkdir -p /neovim && cd /neovim \
    && wget https://github.com/neovim/neovim/releases/download/stable/nvim.appimage \
    && chmod u+x nvim.appimage && ./nvim.appimage --appimage-extract \
    && ln -s "/neovim/squashfs-root/usr/bin/nvim" "/usr/local/bin/nvim" \
    # Install bat-extras \
    && mkdir -p /usr/local/share/bat-extras \
    && git clone https://github.com/eth-p/bat-extras /usr/local/share/bat-extras \
    && cd /usr/local/share/bat-extras \
    && ./build.sh --install \
    && cd ~ \
    # Clean \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

#################################################
# LABELS
# Set metadata.
#################################################
LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "Base image for debian with updates, tools and environment."