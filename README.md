# devcontainers

Experimental devcontainers. 

## What are Development Containers?

</br>

<div id="top"></div>
<div align="center">
  <a href="https://github.com/curol/devcontainers">
    <img src="https://ms-vscode-remote.gallerycdn.vsassets.io/extensions/ms-vscode-remote/remote-containers/0.268.0/1671012609016/Microsoft.VisualStudio.Services.Icons.Default" alt="Logo" width="80" height="80">
  </a>
</div>

</br>

> ![Architecture](https://code.visualstudio.com/assets/docs/devcontainers/containers/architecture-containers.png)


> A Development Container (or Dev Container for short) allows you to use a container as a full-featured development environment. It can be used to run an application, to separate tools, libraries, or runtimes needed for working with a codebase, and to aid in continuous integration and testing. Dev containers can be run locally or remotely, in a private or public cloud.

> The Development Containers Specification seeks to find ways to enrich existing formats with common development specific settings, tools, and configuration while still providing a simplified, un-orchestrated single container option – so that they can be used as coding environments or for continuous integration and testing. Beyond the specification's core metadata, the spec also enables developers to quickly share and reuse container setup steps through Dev Container Features and Templates.

## Developing inside a Container

> The Visual Studio Code Dev Containers extension lets you use a Docker container as a full-featured development environmet. It allows you to open any folder inside (or mounted into) a container and take advantage of Visual Studio Code's full feature set. A devcontainer.json file in your project tells VS Code how to access (or create) a development container with a well-defined tool and runtime stack. This container can be used to run an application or to separate tools, libraries, or runtimes needed for working with a codebase.

> Workspace files are mounted from the local file system or copied or cloned into the container. Extensions are installed and run inside the container, where they have full access to the tools, platform, and file system. This means that you can seamlessly switch your entire development environment just by connecting to a different container.

## Developing on a remote host

When developing on a remote host, you need to use a volume mount for any bind mounts, per [Vscode develop on a remote host](https://code.visualstudio.com/remote/advancedcontainers/develop-remote-host#_converting-an-existing-or-predefined-devcontainerjson).

## Resources

- [VS Code extention](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) - VS Code devcontainers extention.

- [VS Code devcontainers overview](https://code.visualstudio.com/docs/devcontainers/containers) - Official Visual Studio Code development containers docs.

- [VS Code advanced devcontainers](https://code.visualstudio.com/remote/advancedcontainers) - VS Code advanced devcontainers docs.

- [VS Code improve performance](https://code.visualstudio.com/remote/advancedcontainers/improve-performance#_use-a-named-volume-for-your-entire-source-tree) - Improve performance.

- [VS Code command history](https://code.visualstudio.com/remote/advancedcontainers/persist-bash-history) - Persist command history.

- [devcontainers/images](https://github.com/devcontainers/images) - Official devcontainers images.

- [devcontainers/features](https://github.com/devcontainers/features) - Official devcontainers features.

- [devcontainers/feature-starter](https://github.com/devcontainers/feature-starter) - Feature template starter.

- [containers.dev](https://containers.dev/) - Official docs for devcontainers.

- [devcontainer.json reference](https://containers.dev/implementors/json_reference/) - Official `devcontainer.json` reference.