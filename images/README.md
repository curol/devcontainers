# Images

Docker images for the dev containers.

[Working with a github docker registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-docker-registry)

## Common commands

### Login github docker registry

```sh
docker login ghcr.io -u <GITHUB_USERNAME> -p <GITHUB_ACCESS_TOKEN> 
```

### Set Labels in Dockerfile

```dockerfile
LABEL org.opencontainers.image.source "https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_GITHUB_REPO>"

LABEL org.opencontainers.image.description "<YOUR_DESCRIPTION>"
```

### Build image

```sh
npx devcontainer build --workspace-folder <PATH_TO_WORKSPACE>
```

### Change name

```sh
docker tag <CONTAINER_ID> ghcr.io/<GIT_USERNAME>/<GIT_REPO>/<IMAGE_NAME>:<VERSION>
```

### Push image to repo

```sh
docker push ghcr.io/<GIT_USERNAME>/<GIT_REPO>/<IMAGE_NAME>:<VERSION>
```

### Examples

#### Using devcontainer cli

> Build and run devcontainer. 

```sh
npx devcontainer up --workspace-folder <PATH_TO_DEVCONTAINER_WORKSPACE> 
```

> Inspect container

```sh
docker inspect <CONTAINER_ID>
```

> Run interactive terminal in devcontainer.

```sh
docker exec -it --user vscode <CONTAINER_ID> zsh
```

> Go to mounted workspaces 

```sh
cd /workspaces/<PROJECT>
```