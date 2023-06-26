# phoebe_aee
Ansible execution environment for Phoebe HPC system

## Install

Install ansible-builder into python venv:

```
sudo apt install podman
cd python-venv/
python3 -m venv ansible
source ansible/bin/activate
python3 -m pip install --upgrade pip
python3 -m pip install ansible-builder
```

## Use

build:
```
ansible-builder build --verbosity 3 --tag phoebe_aee
```
or with image prune:
```
ansible-builder build --verbosity 2 --prune-images --tag phoebe_aee
```


to see generated images.. `podman images`

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
