# js

JS/TS development container.

## Base Image

`ghcr.io/curol/devcontainers/debian:latest`

## Stack

- Tools
    - ohmyzsh
    - fzf
    - ripgrep
    - fd
    - tree
    - neovim
    - curl
    - bat
    - wget
    - github cli 
    - git

- dotfiles from `curol/dotfiles`

- Nerdfonts

- Non root user: vscode

- Node

- PNPM

- Persist command history

## Getting Started

> Run container in terminal

```
docker run \
--user vscode \
-it \
ghcr.io/curol/devcontainers/js:latest zsh 
```

## Persist Command history 

Persist command history by creating a command history directory and use volume mount to the directory. 
For docs, [VS Code - persist command history](https://code.visualstudio.com/remote/advancedcontainers/persist-bash-history).

> In dockerfile, create command history file and set .zshrc environment variables.

```sh
mkdir /commandhistory
touch /commandhistory/.zsh_history
chown -R $USERNAME /commandhistory
sed -i "s|~/.zsh_history|/commandhistory/.zsh_history|" "${HOME}/.zshrc"
echo "\nexport PROMT_COMMAND='history -a'\n" >> "${HOME}/.zshrc"
```

> Store snippet as string 

```sh
_command_history="$(cat << EOF
mkdir -p /commandhistory
touch /commandhistory/.zsh_history
chown -R $USERNAME /commandhistory
sed -i "s|~/.zsh_history|/commandhistory/.zsh_history|" "${DOTIFLES_DIR}/.zshrc"
echo "\nexport PROMT_COMMAND='history -a'\n" >> "${DOTIFLES_DIR}}/.zshrc"
EOF
)"
```

