# :computer: ROLE dginhoux.docker_registry_image

## :scroll: DESCRIPTION

This ansible role is used to synchronize docker image from publics registries and push them in a local registry.



## :nut_and_bolt: REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform. 
It will skip node with unsupported platform to avoid any compatibility problem.
This behaviour can be bypassed by settings this variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36 |
| EL | 7, 8 |


#### ANSIBLE VERSION

Ansible >= 2.12


#### DEPENDENCIES

None.


## :inbox_tray: INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.docker_registry_image
```

#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.docker_registry_image dginhoux.docker_registry_image
```


## :rocket: USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.docker_registry_image
      ansible.builtin.include_role:
        name: dginhoux.docker_registry_image
      vars:
        docker_cache_registry: localhost:5000
        docker_hub_login: aaa
        docker_hub_password: aaa
        docker_images_list:
          - name: adminer
            state: absent
            tag: 4.8.0-standalone
        docker_python_module:
          - jmespath
          - jsondiff
          - docker
        
```


## :factory: VARIABLES
#### DEFAULT VARIABLES
Role default variables from `defaults/main.yml` : 

| Variable Name | Value |
|---------------|-------|
|docker_hub_login | <pre> aaa </pre> |
|docker_hub_password | <pre> aaa </pre> |
|docker_cache_registry | <pre> localhost:5000 </pre> |
|docker_images_list | <pre> - name: adminer<br>  state: absent<br>  tag: 4.8.0-standalone<br> </pre> |
|docker_python_module | <pre> - jmespath<br>- jsondiff<br>- docker<br> </pre> |


#### CONTEXT VARIABLES

Those variables are located in `vars/*.yml` are used to handle OS differences ; One of theses is loaded dynamically during role
runtime using the `include_vars` module and set OS specifics variable's.





## :man: AUTHOR

[![Author](https://img.shields.io/badge/maintained%20by-dginhoux-e00000?style=flat-square)](https://github.com/dginhoux)


## :bookmark_tabs: LICENSE

[![License](https://img.shields.io/github/license/dginhoux/ansible_role.docker_registry_image?style=flat-square)](https://github.com/dginhoux/ansible_role.docker_registry_image/blob/master/LICENSE)