Ansible Role : dginhoux.docker_registry_image
=========

This ansible role is used to synchronize docker image from publics registries and push them in a local registry.


Requirements
------------

This role is built to only run on platforms defined in `meta/main.yml`


Role Variables
--------------

```yaml
docker_hub_login: "aaa"
docker_hub_password: "aaa"

docker_cache_registry: "localhost:5000"

docker_images_list:
  - { state: "absent", name: "adminer", tag: "4.8.0-standalone" }

```

Dependencies
------------

Docker engine need to be installed on the node where this roles is running.


Example Playbook
----------------



License
-------

BSD


Author Information
------------------

https://github.com/dginhoux/
