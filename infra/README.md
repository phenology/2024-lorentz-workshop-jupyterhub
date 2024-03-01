# DockerHub deployment scripts

The deployment scripts are based on the ones from [JupyterDockerSpawnerOnSRC](https://github.com/RS-DAT/JupyterDockerSpawnerOnSRC)

## Create a "Component"

## Create a "Catalog Item"

## Create a Workspace

Run this multiple times to create more JupyterHub instances.

## Add users to the deployment

Once the workspace(s) is/are running, add a list of (random) users to the workspaces using the following steps:

* Install ansible locally, e.g. in a new environment:
  ```shell
  mamba create -c conda-forge -n ansible python=3.11 ansible passlib
  mamba activate ansible
  ```

* Create the list of the workspaces that you want to configure. Use the template [`hosts.template`](./hosts.template), naming the file `hosts`. Both workspaces' IPs and hostnames can be used here (both are available from the dashboard in the Research Cloud portal).

* Create the list of usernames and passwords to be added to the workspaces. Use the template [`hosts.template`](users.yml.template), naming the file `users.yml`. Passwords can be randomly generated using e.g.:

  ```shell
  tr -dc A-Za-z0-9 </dev/urandom | head -c 8
  ```

* Run ansible (note that the path to the private key used for SRAM needs to be adapted):

  ```shell
  ansible-playbook -i hosts --key-file /path/to/the/private/key add-users.yml
  ```

