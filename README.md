# phoebe_aee

Ansible execution environment for Phoebe HPC system.
For python environment `uv` tool is used.

## Dependencies

### System

- `podman` ( `sudo apt install podman`)
- `uv` (`curl -LsSf https://astral.sh/uv/install.sh | sh`)

### Procedural

- make sure you have github access token with write access to your package registry

## Use

### Build the ansible environment

```
uv run ansible-builder build --verbosity 2 --tag phoebe_aee
```

(possibly with prune-images):

```
uv run ansible-builder build --no-cache --prune-images -v 3 --tag phoebe_aee
```
### See podman images at current system:

```
podman images
```

### Upload your package to github package registry

..login to ghcr with github userame and personal access token:

```
podman login ghcr.io
```

..and upload to package registry:

```
podman push localhost/phoebe_aee ghcr.io/jose-d/phoebe_aee:latest
```

## Other

Save the image into tarball:

```
podman save --quiet -o phoebe_aee-1.0.tar localhost/phoebe_aee
```
