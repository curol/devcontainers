
#################################################
# BASE IMAGE 
#################################################
FROM ghcr.io/curol/devcontainers/debian:latest

#################################################
# RUN
# Install tools and create the user environment.
#################################################
ARG USERNAME=vscode
ARG HOME=/home/$USERNAME
ARG NODE_VERSION=18
ARG PNPM_STORE_DIR="$HOME/.local/share/pnpm/store"
ARG PNPM_VER=latest
ARG PNPM_GLOBAL_PACKAGES="vercel"
ARG TERM=xterm-256color

# ARG NERDFONTS_COMMAND="curl --output-dir $XDG_FONTS_DIR -fLo "${NFONT_NAME}" https://github.com/ryanoasis/nerd-fonts/raw/HEAD/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf"
# If you want a global pnpm store
# ARG PNPM_STORE_COMMAND="su $USERNAME -s /usr/bin/zsh -c \"pnpm config set store-dir $PNPM_STORE_DIR\""

RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update && apt-get -y upgrade \
    && cd ${HOME} \
    # Install dotfiles \
    && git clone https://github.com/curol/dotfiles \
    # Setup command history \
    && mkdir -p /commandhistory \
    && touch /commandhistory/.zsh_history \
    && sed -i "s|~/.zsh_history|/commandhistory/.zsh_history|" "${HOME}/dotfiles/.zshrc" \
    && echo "\nexport PROMT_COMMAND='history -a'\n" >> "${HOME}/dotfiles/.zshrc" \
    && chown -R "${USERNAME}:${USERNAME}" /commandhistory \
    # Sync dotfiles \
    && dotfiles/install.sh overwrite -f \
    # Set ownership for home \
    && chown -R "${USERNAME}:${USERNAME}" $HOME/.* \
    && chown -R "${USERNAME}:${USERNAME}" $HOME/* \
    # Source environment variables \
    && . $HOME/.exports \
    # Change login shell \
    && chsh -s /usr/bin/zsh $USERNAME \
    # Install node \
    && curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION}.x | sudo bash - \
    && apt-get update && apt-get install -y nodejs \
    # Enable corepack and install pnpm \
    && chown -R ${USERNAME}:${USERNAME} ${HOME} \
    && corepack enable \
    && su $USERNAME -c "corepack prepare pnpm@$PNPM_VER --activate" \
    && su $USERNAME -s /usr/bin/zsh -c 'pnpm setup' \
    # && ${PNPM_STORE_COMMAND} \
    # Create workspace directory \
    && mkdir -p /workspaces \
    && chown -R "${USERNAME}:${USERNAME}" /workspaces \
    # Clean \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /root/.gnupg /tmp/library-scripts

#################################################
# LABELS
# Set metadata.
#################################################
LABEL org.opencontainers.image.source "https://github.com/curol/devcontainers"
LABEL org.opencontainers.image.description "JS/TS development environment."