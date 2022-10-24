# ROLE dginhoux.docker_registry_image



## DESCRIPTION

This ansible role is used to synchronize docker image from publics registries and push them in a local registry.
<br />
Authentification is supported.
<br />
It use an external tools, already included (in `files/`) with this role : https://github.com/andrey-pohilko/registry-cli

## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip node with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.12

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.docker_registry_image
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.docker_registry_image dginhoux.docker_registry_image
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.docker_registry_image
      ansible.builtin.include_role:
        name: dginhoux.docker_registry_image
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml

## external tools necessary for manage registry from cli
## this role cannot be used without
## https://github.com/andrey-pohilko/registry-cli#garbage-collection-in-docker-registry
docker_registry_cli_install: true
docker_registry_cli_path: /opt/registry_cli


docker_default_remote_registry_auth: true
docker_default_remote_registry_scheme: https
docker_default_remote_registry_url: docker.io
docker_default_remote_registry_login: aaa
docker_default_remote_registry_password: qqq


docker_default_cache_registry_auth: false
docker_default_cache_registry_scheme: http
docker_default_cache_registry_url: registry-cache.infra.ginhoux.net:5000
docker_default_cache_registry_login: ""
docker_default_cache_registry_password: ""


docker_images_list:
  # - name: aaa
  #   remote_registry_auth: true
  #   remote_registry_scheme: https
  #   remote_registry_url: 
  #   remote_registry_login: 
  #   remote_registry_password: @
  #   cache_registry_auth: false
  #   cache_registry_scheme: http
  #   cache_registry_url: 
  #   cache_registry_login: 
  #   cache_registry_password: 
  #   tags_absent: [ ]
  #   tags_present: [ ]

  - name: authelia/authelia
    tags_absent: [ 4.36.4, 4.36.5, 4.36.6 ]
    tags_present: [ 4.36.7, 4.36.8 ]

  - name: caddy
    tags_absent: [ 2.4.0-alpine, 2.4.3-alpine, 2.4.5-alpine, 2.4.6-alpine ]
    tags_present: [ 2.5.1-alpine, 2.5.2-alpine, 2.6.0-alpine, 2.6.1-alpine, 2.6.2-alpine ]

  - name: cadvisor/cadvisor
    remote_registry_auth: false
    remote_registry_scheme: https
    remote_registry_url: gcr.io
    tags_absent: [ v0.39.0, v0.40.0 ]
    tags_present: [ v0.45.0 ]

  - name: grafana/grafana
    tags_absent: [ 9.1.6, 9.1.7, 9.1.8 ]
    tags_present: [ 9.2.0, 9.2.1 ]


docker_python_module:
  - jmespath
  - jsondiff
  - docker
```


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux

## LICENSE

MIT
<br />
Refer to https://github.com/andrey-pohilko/registry-cli for registry-cli license
