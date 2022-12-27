# Images

Docker images for the dev containers.

## Creating a package for a github repo

[Working with a github docker registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-docker-registry)

### Set Labels in Dockerfile

```dockerfile
LABEL org.opencontainers.image.source "https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_GITHUB_REPO>"

LABEL org.opencontainers.image.description "<YOUR_DESCRIPTION>"
```

### Login github docker registry

```sh
docker login ghcr.io -u <GITHUB_USERNAME> -p <GITHUB_ACCESS_TOKEN> 
```

### Build devcontainer

```sh
devcontainer build --workspace-folder <PATH_TO_WORKSPACE>

docker tag <IMAGE_ID> ghcr.io/<GIT_USERNAME>/<GIT_REPO>/<IMAGE_NAME>:<VERSION>
```

### Push image to repo

```sh
docker push ghcr.io/<GIT_USERNAME>/<GIT_REPO>/<IMAGE_NAME>:<VERSION>
```
