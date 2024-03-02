# FAIR Phenological Modelling - JupyterHub

This repository includes material to deploy [JupyterHub](https://jupyter.org/hub) on [SURF Research Cloud (SRC)](https://www.surf.nl/en/services/surf-research-cloud), specifically designed for the 2024 Lorentz Workshop: [FAIR Phenological Modelling](https://www.lorentzcenter.nl/fair-phenological-modelling.html).

The repository is organized as follows:

* [`infra`](./infra) contains ansible playbooks and other scripts employed to deploy the JupyterHub service on SRC. They are based on the playbooks from the [JupyterDockerSpawnerOnSRC](https://github.com/RS-DAT/JupyterDockerSpawnerOnSRC) repository. The JupyterHub [DockerSpawner](https://jupyterhub-dockerspawner.readthedocs.io) is used to spawn Jupyter instances for the users who log in to the Hub. 
* [`image`](./image) contains the Dockerfile and other material used to build the image used by the Hub. Note that the image building is automated using GitHub Actions (see the [`.github/workflows/build-image.yml`](.github/workflows/build-image.yml) workflow file). The image is pushed to the GitHub Container Registry as  [ghcr.io/phenology/2024-lorentz-workshop-jupyterhub](https://github.com/phenology/2024-lorentz-workshop-jupyterhub/pkgs/container/2024-lorentz-workshop-jupyterhub). 

