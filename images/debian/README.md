# debian

Simple Debian container with common tools.

## Features

- common-utils
- github-cli
- git

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

- Non root user: vscode

- Dotfiles skeleton

- Command history skeleton

## Getting Started

> Run container as root in terminal.

```sh
docker run -it ghcr.io/curol/devcontainers/debian:latest bash
```

> Run container as user vscode in terminal.

```sh
docker run --user vscode -it ghcr.io/curol/devcontainers/debian:latest zsh 
```
