FROM ghcr.io/curol/devcontainers/base-debian:latest

ARG USERNAME=${USERNAME}
ARG HOME=/home/$USERNAME
ARG DOTFILES=${DOTFILES}
ARG WORKSPACE_PATH=${WORKSPACE_PATH}
ARG TERM=xterm-256color

RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update && apt-get -y upgrade \
    && cd "${HOME}" \
    # Install dotfiles \
    && git clone "${DOTFILES}" \
    # Setup command history \
    && mkdir -p /commandhistory \
    && touch /commandhistory/.zsh_history \
    && sed -i "s|~/.zsh_history|/commandhistory/.zsh_history|" "${HOME}/dotfiles/.zshrc" \
    && echo "\nexport PROMPT_COMMAND='history -a'\n" >> "${HOME}/dotfiles/.zshrc" \
    && chown -R "${USERNAME}:${USERNAME}" /commandhistory \
    # Install dotfiles \
    && dotfiles/install.sh overwrite -f \
    # Set ownership for home \
    && chown -R "${USERNAME}:${USERNAME}" $HOME/.* \
    && chown -R "${USERNAME}:${USERNAME}" $HOME/* \
    # Source environment variables \
    && . $HOME/.exports \
    # Change login shell \
    && chsh -s /usr/bin/zsh $USERNAME \
    # Create workspace directory \
    && mkdir -p ${WORKSPACE_PATH} \
    && chown -R "${USERNAME}:${USERNAME}" ${WORKSPACE_PATH} \
    # Clean \
    && chown -R ${USERNAME}:${USERNAME} ${HOME} \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "Debian development environment."