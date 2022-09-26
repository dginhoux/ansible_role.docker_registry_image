# ROLE dginhoux.docker_registry_image



## DESCRIPTION

This ansible role is used to synchronize docker image from publics registries and push them in a local registry.



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
docker_hub_login: "aaa"
docker_hub_password: "aaa"
docker_cache_registry: "localhost:5000"
docker_images_list:
  - { state: "absent", name: "adminer", tag: "4.8.0" }
  - { state: "present", name: "redis", tag: "6.2.8" }
  - { state: "present", name: "mariadb", tag: "10.5" }

docker_python_module:
  - jmespath
  - jsondiff
  - docker

```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
